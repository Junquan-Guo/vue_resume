<template>
  <!-- 能力 -->
  <section class="skill fp-section" style="">
    <div class="content">
      <div class="skill-circle">
        <ul class="out">
          <li class="item" v-for="item in out" :style="item.icon">{{item.skill}}</li>
        </ul>
        <ul class="inner">
          <li class="inner-item" v-for="item in inner" :style="item.icon">{{item.skill}}</li>
        </ul>
      </div>
      <div class="des">
        <p v-for="site in introduce">{{site.referral}}</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Skill',
  data () {
    return {
      out:[
          {skill:'webpack',icon:'background-color: rgba(121, 100, 102, 0.8);'},
          {skill:'gulp',icon:'background-color: rgba(49, 65, 82, 0.8);'},
          {skill:'sass',icon:'background-color: rgba(76, 157, 160, 0.8);'},
          {skill:'小程序',icon:'background-color: rgba(66, 66, 66, 0.8);'},
          {skill:'node',icon:'background-color: rgba(193, 131, 106, 0.8);'},
          {skill:'ES6',icon:'background-color: rgba(117, 148, 179, 0.8);'},
          {skill:'Git',icon:'background-color: rgba(71, 83, 94, 0.8);'},
          {skill:'vue',icon:'background-color: rgba(147, 147, 189, 0.8);'}
        ],
        inner:[
          {skill:'layui',icon:'background-color: rgba(179, 164, 140, 0.8);'},
          {skill:'bootstrap',icon:'background-color: rgba(238, 215, 163, 0.8);'},
          {skill:'asp.net',icon:'background-color: rgba(171, 209, 220, 0.8);'},
          {skill:'jQuery',icon:'background-color: rgba(207, 184, 178, 0.8);'},
        ],
        introduce:[
          {referral:'一年前端开发经验'},
          {referral:'精通 HTML5、CSS3（布局）、JavaScript、ajax、jQuery、了解ES6语法；'},
          {referral:'熟练使用vue（Vue2+vue-router+vuex+axios）全家桶相关技术；'},
          {referral:'熟悉小程序，bootstrap、layui等UI框架，了解Node.js；'},
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
.skill
  background: #4d5e8f

  .content 
    position: absolute
    top: 15vh
    left: 5vw
    right: 5vw
    display: flex
    align-items: center
    flex-wrap: wrap
    justify-content: center
    color: #fff
    text-align: center

    .skill-circle 
      padding: .15625rem
      position: relative
      font-size: .5625rem

      @mixin animation($type1,$duration1,$type2,$duration2) 
            animation: $type1 8s cubic-bezier(0.36, 0, 0.64, 1) $duration1 infinite alternate, $type2 8s cubic-bezier(0.36, 0, 0.64, 1) $duration2 infinite alternate
            @keyframes outX 
              0% 
                left:  -1.5625rem

              100% 
                left: 14.0625rem

            @keyframes outY 
              0% 
                top:  -1.5625rem

              100% 
                top: 14.0625rem

            @keyframes innerX 
              0% 
                left: -1.25rem
       
              100% 
                left: 8.125rem
   

            @keyframes innerY 
              0% 
                top: 8.125rem
              
              100%
                top: -1.25rem

      .out 
        width: 15.625rem
        height: 15.625rem
        border: .25rem dashed #999
        border-radius: 50%
        position: relative
        margin: 0 auto

        .item 
          width: 3.125rem
          height: 3.125rem
          border-radius: 50%
          position: absolute
          text-align: center
          line-height: 3.125rem
          background: red
          -webkit-backface-visibility: hidden

          &:nth-child(1) 
            @include animation(outX, -4s, outY, 0s)
  
          &:nth-child(2) 
            @include animation(outX, -6s, outY, -2s)
              
          &:nth-child(3) 
            @include animation(outX, -8s, outY, -4s);
              
          &:nth-child(4) 
            @include animation(outX, -10s, outY, -6s);

          &:nth-child(5) 
            @include animation(outX, -12s, outY, -8s);

          &:nth-child(6) 
            @include animation(outX, -14s, outY, -10s);

          &:nth-child(7) 
            @include animation(outX, -16s, outY, -12s);

          &:nth-child(8) 
            @include animation(outX, -18s, outY, -14s);
   
        
      .inner 
        width: 9.375rem
        height: 9.375rem
        border: .25rem dashed #999
        border-radius: 50%
        position: absolute
        text-align: center
        line-height: 1.5625rem
        top: 50%
        left: 50%
        transform: translateX(-50%) translateY(-50%)

        .inner-item 
          width: 2.5rem;
          height: 2.5rem;
          border-radius: 50%;
          position: absolute;
          text-align: center;
          line-height: 2.5rem;
          background: red;
          -webkit-backface-visibility: hidden;

          &:nth-child(1)
            @include animation(innerX, -4s, innerY, 0s)

          &:nth-child(2) 
            @include animation(innerX, -8s, innerY, -4s)
              
          &:nth-child(3) 
            @include animation(innerX, -12s, innerY, -8s)
              
          &:nth-child(4) 
            @include animation(innerX, -16s, innerY, -12s)
    
    .des 
      margin-top: 3.125rem
      line-height: 1.25rem
      font-size: .8125rem

      p
        margin: 1rem 0
</style>
