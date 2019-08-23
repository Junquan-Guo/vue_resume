<template>
  <!-- 联系我 -->
  <section class="contact fp-section">
    <div class="content">
      <div class="words">
        <span v-for="item in words">{{item.title}}</span>
      </div>
      <div class="idea">
        <p v-for="item in idea">{{item.line}}</p>
      </div>
      <div class="way">
        <a class="way-item" target="_blank" v-for="item in way" :href="item.url">
          <img class="way-item-img" alt :src="item.icon"/>
        </a>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Contact",
  data() {
    return {
      words: [
        {title:'灵感'},
        {title:'代码'},
        {title:'梦想'},
        {title:'未来'}
      ],
      idea:[
        {line:'注重效率，偏爱敏捷开发'},
        {line:'喜欢尝试，期待新鲜事物'},
        {line:'前端即兴趣，兴趣即未来'},
        {line:'行路有良友，便是捷径'},
        {line:'带上我吧，一起看到更大的世界'}
      ],
      way:[
        {
          icon: require('../assets/images/s_github.svg'),
          url:'https://github.com/Junquan-Guo'
        },
        {
          icon: require('../assets/images/s_blog.svg'),
          url:'https://gitee.com/ceartmy/projects'
        },
        {
          icon: require('../assets/images/s_sf.svg'),
          url:'https://segmentfault.com/u/qianduanxiaoguo'
        },
        {
          icon: require('../assets/images/s_yx.svg'),
          url:'http://mail.qq.com/cgi-bin/qm_share?t=qm_mailme&email=GyojLCooKSojLC1bamo1eHR2'
        },
        {
          icon: require('../assets/images/s_lx.svg'),
          url:'https://wpa.qq.com/msgrd?v=3&uin=1871321876&site=qq&menu=yes'
        }
      ]
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
.contact 
  background: #a29971

  .content 
    position: absolute
    top: 15vh
    left: 10vw
    right: 10vw
    margin: 0 auto
    text-align: center
    color: #fff

    .words 
      font-size: 1.125rem
      margin: 0 auto
      display: flex
      justify-content: space-between

      span
        &:first-child 
          color: red

        &:nth-child(2) 
          color: #3cf

        &:nth-child(3) 
          color: #6c0

        &:nth-child(4) 
          color: #f63

    .idea 
      margin-top: 3.125rem

    .way 
      display: flex
      justify-content: space-around
      margin: 3.125rem auto 0
      width: 70vw

      .way-item 
        border-radius: 50%
        border: 2px solid #fff
        width: 1.875rem
        height: 1.875rem
        position: relative

        .way-item-img 
          width: 65%
          position: absolute
          top: 50%
          right: 50%
          transform: translateX(50%) translateY(-50%)

</style>
