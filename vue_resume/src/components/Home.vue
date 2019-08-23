<template>
  <!-- 首页 -->
  <section class="overview fp-section ">
    <div class="content">
      <div class="info">
        <div class="photo"></div>
        <ul class="-list">
          <li class="-item">{{item.age}}</li>
          <li class="-item">{{item.education}}</li>
          <li class="-item">{{item.site}}</li>
          <li class="-item">{{item.state}}</li>
        </ul>
      </div>
      <div class="des">
        <p class="quote">{{Saying}}</p>
        <div class="des-list">
          <p v-for="site in introduce">{{site.referral}}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      item:{
        age: '22岁',
        education: '专科',
        site: '广州',
        state: '在职',
      },
      Saying:'生活是一种绵延不绝的渴望，渴望不断上升，变得更伟大而高贵。',
      introduce:[
        {
          referral:'我叫郭俊权，前端工程师'
        },
        {
          referral:'广州炘楠文化传播有有限公司'
        },
        {
          referral:'15914967410@163.com'
        }
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
.overview 
  background: #87b0a5

  .content 
    position: absolute
    top: 10vh
    left: 5vw
    right: 5vw

    .info 
      margin-top: 10vh
      position: relative

      .photo 
        width: 9.375rem
        height: 9.375rem
        border-radius: 50%
        margin: 0 auto
        background: url(../assets/images/photo.jpg) no-repeat 50%
        background-size: contain
        transition: box-shadow .5s linear

      .-list 
        position: absolute
        top: 50%
        left: 50%
        width: 3.125rem
        height: 3.125rem
        transform: translateX(-50%) translateY(-50%)

        .-item 
          position: absolute
          top: 0
          left: 0
          width: 3.125rem
          height: 3.125rem
          line-height: 3.125rem
          border-radius: 50%
          text-align: center
          color: #fff
          font-size: .8125rem
          box-shadow: inset 0 0 1.5625rem 0.3125rem hsla(0,0%,100%,.67)
          animation: pulse 2s linear infinite

          @keyframes pulse 
            0% 
              transform: scaleX(1)
            50% 
              transform: scale3d(1.1, 1.1, 1.1)
            to 
              transform: scaleX(1)

          &:nth-child(1) 
            top: -190%
            left: -170%
              
          &:nth-child(2) 
            top: 120%
            left: -220%
            width: 3.125rem
            height: 3.125rem
            line-height: 3.125rem

          &:nth-child(3) 
            top: -170%
            left: 170%
            width: 3.4375rem
            height: 3.4375rem
            line-height: 3.4375rem

          &:nth-child(4) 
            top: 100%
            left: 210%
            width: 3.28125rem
            height: 3.28125rem
            line-height: 3.28125rem

    .des 
      text-align: center
      margin: 0 auto
      padding-top: 3.125rem
      color: #fff

      .quote 
        font-size: 1rem
        line-height: 1.5625rem
        position: relative
        padding: .625rem 0

        &:after 
          content: ""
          position: absolute
          left: 0
          right: 0
          bottom: 0
          height: 1px
          background-color: hsla(0,0%,100%,.6)

      .des-list 
        padding-top: .625rem
        font-size: .9375rem

        p
          margin: 1rem 0

</style>
