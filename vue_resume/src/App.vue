<template>
  <div id="app" @mousewheel="mouse">
    <Header v-bind:collectionIndex="init" v-on:childById="childById"/>
    <!-- main -->
    <main id="fullpage" class="fp-root">
      <Home :class='init===0? "fp-cur-page":""' /><!-- 首页-end -->
      <Skill :class='init===1? "fp-cur-page":""'/><!-- 能力-end -->
      <Experience :class='init===2? "fp-cur-page":""'/><!-- 经历-end -->
      <Work :class='init===3? "fp-cur-page":""'/><!-- 作品集 -end-->
      <Contact :class='init===4? "fp-cur-page":""' /><!-- 联系我-end -->
      <div class="fp-arrow" :style="{display:(init==0?'none':'block')}" @click="btn(init)"></div>
    </main>
    <Footer v-show="init === 4"/>
  </div>
</template>

<script>
import device from "./assets/js/index.js";

import Header from './components/Header'
import Footer from './components/Footer'
import Home from './components/Home'
import Skill from './components/Skill'
import Experience from './components/Experience'
import Work from './components/Work'
import Contact from './components/Contact'

export default {
  name: 'App',
  components: {
    Header,Footer,Home,Skill,Experience,Work,Contact
  },
  data () {
    return {
      init: 0,
      lastscroll: 0,
    }
  },
  methods: {
    childById: function (childId) {
      // childValue就是子组件传过来的值
      this.init = childId
    },
    btn(init) {
      this.init=init-1
    },  
    mouse (event) {
      // 防止用户短时间内滚动多次，设置滚动间隔大于一秒才能生效
      // 判断滚动间隔时间
      let scrollduration = event.timeStamp - this.lastscroll
      console.log(scrollduration)
      if (scrollduration > 1000) {
        // 将这一次的滚动时间记录为上一次合法的滚动时间
        this.lastscroll = event.timeStamp
        console.log('合法的滚动')
        // 判断滚动方向进行操作
        if (event.deltaY > 0) {
          console.log('down')
          if (this.init === 4) 
            return ;
          this.init = this.init + 1

        } else {
          console.log('up')
          if (this.init === 0) 
            return ;
          this.init = this.init - 1
        }
      } else {
        // 如果滚动不合法就不做任何操作
        console.log('请爱护你的鼠标不要连续滚动！')
      }
    }
  },
  mounted () {
    this.clientHeight = `${document.documentElement.clientHeight}px`
    // 然后监听window的resize事件．在浏览器窗口变化时再设置下背景图高度
    window.onresize = () => {
      this.clientHeight = `${document.documentElement.clientHeight}px`
      console.log(this.clientHeight)
    }
  }
}
</script>

<style lang="sass">
@import './assets/style/base.css'
@import './assets/style/media.scss'

p
 margin: 1rem 0

main 
  display: block

  .fp-arrow 
    position: absolute
    bottom: 20px
    width: 20px
    height: 35px
    left: 50%
    z-index: 100
    background: url(data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBzdGFuZGFsb25lPSJubyI/PjwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+PHN2ZyB0PSIxNDkwMjM2MzkyNTUyIiBjbGFzcz0iaWNvbiIgc3R5bGU9IiIgdmlld0JveD0iMCAwIDEwMjQgMTAyNCIgdmVyc2lvbj0iMS4xIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHAtaWQ9IjE4MDg1IiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgd2lkdGg9IjIwMCIgaGVpZ2h0PSIyMDAiPjxkZWZzPjxzdHlsZSB0eXBlPSJ0ZXh0L2NzcyI+PC9zdHlsZT48L2RlZnM+PHBhdGggZD0iTTQ4OS41NyAyNDkuMzQ0bC00NzkuMTU3IDQ3OS4xMjJjLTEzLjkwNyAxMy45NDMtMTMuOTA3IDM2LjQ4IDAgNTAuNDIyIDEzLjk0MyAxMy45NDMgMzYuNTE1IDEzLjk0MyA1MC40NTggMGw0NTUuNzY1LTQ1NS43MyA0NDguMjQxIDQ0OC4yMDVjMTMuNTE2IDEzLjU1MSAzNS40NDYgMTMuNTUxIDQ4Ljk2MSAwIDEzLjU4Ni0xMy41MTUgMTMuNTg2LTM1LjQ0NiAwLTQ4Ljk5NWwtNDY1LjQ2NC00NjUuNWMtMS44MTktMS44MTktNC4wMzAtMi43MS02LjEzMy00LjAzMC0wLjgyLTEuMTA1LTEuMjQ4LTIuNDYxLTIuMjgyLTMuNDk1LTEzLjkwNy0xMy45MDctMzYuNDgtMTMuOTA3LTUwLjM4NyAweiIgcC1pZD0iMTgwODYiIGZpbGw9IiNmZmZmZmYiPjwvcGF0aD48L3N2Zz4=) no-repeat bottom center
    background-size: contain
    pointer-events: none
    transform: translateX(-50%)
    animation: arrowAnimate 1.5s ease-in-out infinite
    cursor: pointer

    @keyframes arrowAnimate
      0% 
        bottom: 10px
        opacity: 0.8
      50% 
        bottom: 20px
        opacity: 1
      80% 
        bottom: 22px
        opacity: 0.4
      100% 
        bottom: 22px
        opacity: 0

.fp-root 
  position: absolute
  top: 0
  left: 0
  right: 0
  bottom: 0
  background: #eee
  overflow: hidden

.fp-section 
  position: absolute
  top: 0
  left: 0
  right: 0
  bottom: 0
  overflow: hidden
  display: none

.fp-cur-page 
  z-index: 10
  display: block
</style>
