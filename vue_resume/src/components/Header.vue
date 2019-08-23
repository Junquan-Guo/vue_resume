<template>
  <!-- header -->
  <header class="header">
    <div class="title-c"  v-for="(list,index) in titleList" :key="index" v-if="index===collectionIndex && collectionIndex!=0">
      <div :class="nav ? 'title' : 'title -rotate' " @click="btn(index)">{{list.title}}</div>
      <div class="title-pc" style="display: block;">{{list.title}}</div>
    </div>
    <div class="language">
      <div class="-c">
        <span class="-item -selected">中</span>
        <span class="-item">英</span>
      </div>
    </div>
    <div :class="nav ? 'nav' : 'nav show-nav' " >
      <ul class="-list">
        <li v-for="(list,index) in titleList"  :key="index" :class="{active:index==collectionIndex}" @click="btn(index)">
          <span>{{list.title}}</span>
        </li>
      </ul>
    </div>
    <div class="nav-dot">
      <ul>
        <li class="nav-dot-item" v-for="(list,index) in titleList"  :key="index" :class="{active:index==collectionIndex}"  @click="btn(index)">
          <em>
            <img alt :src="list.svg" />
          </em>
          <span class="-title">{{list.title}}</span>
        </li>
      </ul>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      nav:false,
      childId: 0,
      titleList: [
        {
          svg: require('../assets/images/d_home.svg'),
          title: '首页'
        },
        {
          svg: require('../assets/images/d_skills.svg'),
          title: '能力'
        },
        {
          svg: require('../assets/images/d_exp.svg'),
          title: '经历'
        },
        {
          svg: require('../assets/images/d_works.svg'),
          title: '作品集'
        },
        {
          svg: require('../assets/images/d_contact.svg'),
          title: '联系我'
        }
      ]
    }
  },
  props:['collectionIndex'],
  methods: {
    btn(index) {
      this.nav=!this.nav
      this.$emit('childById', index)
    }  
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
header 
  z-index: 1000
  right: 0
  left: 0
  top: 0
  height: 3.75rem
  position: absolute

  .title-c 
    width: 100%
    height: 3.75rem
    position: absolute
    display: flex
    justify-content: center
    align-items: center
    color: #fff

    .title 
      position: relative
      cursor: pointer

      &:after 
        content: ""
        position: absolute
        top: 50%
        right: -.9375rem
        width: 0
        height: 0
        border-left: .3125rem solid transparent
        border-right: .3125rem solid transparent
        border-top: .3125rem solid #fff
        transition: .5s

    .-rotate
      &:after 
        transform: rotate(180deg)

    .title-pc 
      display: none
      text-align: center
      position: relative
      top: 1.875rem

  .language 
    position: absolute
    height: 3.75rem
    right: 3vw
    display: flex
    align-items: center
    cursor: pointer

    .-c 
      border-radius: .78125rem
      background-color: rgba(0,0,0,.1)
      position: relative

      .-item 
        color: rgba(0,0,0,.3)
        width: 1.875rem
        line-height: 1.875rem
        display: inline-block
        text-align: center
        transition: color .3s ease

      .-selected 
        color: #fff

      &:after 
        content: ""
        width: 1.875rem
        height: 1.875rem
        background-color: rgba(0,0,0,.75)
        position: absolute
        top: 0
        left: 0
        transform: translateX(0)
        border-radius: 50%
        z-index: -1
        transition: transform .3s ease

  .nav 
    height: 1.875rem
    position: absolute
    top: 3.125rem
    width: 100%
    font-size: .40625rem
    background-color: hsla(0,0%,100%,.4)
    visibility: hidden
    opacity: 0
    transition: all .5s

    .-list 
      justify-content: space-around
      align-items: center
      display: flex
      height: 1.875rem
      font-size: .8125rem

      li
        cursor: pointer

      .active
        color: #38bcff
  
  .show-nav 
    visibility: visible
    opacity: 1

  .nav-dot 
    display: none
    position: fixed
    top: 50%
    transform: translateY(-50%)
    text-align: center

    .nav-dot-item 
      position: relative

      em 
        position: absolute
        top: 50%
        transform: translateY(-50%)
        background: rgba(0,0,0,.7)
        transition: all .3s ease
        border-radius: 50%
        opacity: .1
        cursor: pointer

        &:hover 
          transform: translateY(-50%) scale(3)
          opacity: 1

          &+span,img 
            opacity: 1

        img 
          width: 60%
          opacity: 0
          position: absolute
          top: 50%
          right: 50%
          transform: translateY(-50%) translateX(50%)
          z-index: -1
          pointer-events: none
      
      .-title 
        position: absolute
        display: inline-block
        opacity: 0
        z-index: 1
        transition: all .3s ease
        text-align: center
        background: rgba(0,0,0,.7)
        color: #fff
        font-weight: 700

        &:after 
          content: ""
          position: absolute
          right: -12PX
          width: 0
          height: 0
          border-top: 12px solid transparent
          border-left: 12px solid rgba(0,0,0,.7)
          border-bottom: 12px solid transparent
    
    .active

      em 
        transform: translateY(-50%) scale(3)
        opacity: 1

        img 
          opacity: 1
</style>
