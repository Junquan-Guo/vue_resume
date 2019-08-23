<template>
  <!-- 作品集 -->
  <section class="work fp-section">
    <div class="content">
      <ul class="work-list">
        <li class="work-list-item" v-for="(list,index) in worksList" :key="index" :style="index-presentId>=0?'transform: translateX(' + (lateX+1.5*(index-presentId))+'rem) translateZ('+(lateZ-(1.5*index-presentId))+'rem) scale('+(scale-0.05*(index-presentId))+','+(scale-0.05*(index-presentId))+')':'transform: translateX(-19rem) translateZ(-15rem)'">
          <div class="-title">
            <a class="-link" :href="list.url">{{list.title}}</a>
          </div>
          <p class="-des">{{list.des}}</p>
          <div class="-qrcode" v-if="list.mini">
            <img class="-img" :src="list.mini" />
            <p class="-des">（微信内长按识别）</p>
          </div>
          <div class="work-link" v-if="list.url">
            <a class="-img" :href="list.url" target="_blank"></a>
            <p class="-des" v-if='list.url.indexOf("quickapp")>-1'>（安卓浏览器可跳转）</p>
          </div>
        </li>
      </ul>
      <div class="more">
        <a :href="viewMore.url" target="_blank">{{viewMore.title}}</a>
      </div>
      <div class="switch">
        <i class="left" :style="{filter:(presentId==0?'brightness(70%)':'')}" @click="previousPage(presentId)"></i>
        <i class="right" :style="{filter:(presentId== this.finally-1 ?'brightness(70%)':'')}" @click="nextPage(presentId)"></i>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Work",
  data() {
    return {
      worksList: [
        {
          title: '亿众童年 小程序',
          des: ' 该小程序主要为广东广播电视台中国小金钟比赛提供支持，小程序主要由资讯、投票、报名、会员四个部分组成。',
          mini: require('../assets/images/w_yz.jpg')
        },
        {
          title: '樊易林国学馆 PC端',
          des: '樊易林国学馆主要是进行文化传播，及时更新动态，以国学为主导，易学、字画、文玩等多维度的专用信息知识咨询。',
          url: 'http://www.gz-fyl.com/'
        },
        {
          title: '樊易林国学馆 移动端',
          des: 'asp.net + SQLserver + jQuery,采用淘宝flexible布局，基于手机h5网页，为销售途径提供新的渠道。',
          url: 'http://www.gz-fyl.com/Mobile/Default'
        },
        {
          title: 'Node个人博客 Layui',
          des: '采用Node.js + express框架 + Mongodb数据库构建的一个博客，用Layui实现多端使用，flow流加载来展示文章。',
          url: 'https://gitee.com/ceartmy/Node_demo'
        },
        {
          title: '仿vivo手机商城 Vue',
          des: 'Vue2 + vuex +axios +vue-router + vant,使用vuex状态管理来实现用户收藏，购物车，文章点赞，升降等功能。',
          url: 'http://vivo.yangzhiping.site/#/'
        },
        {
          title: 'asp.net校约健 bootstrap',
          des: 'bootstrap框架 + Python爬虫 + SQLserver + ASP.net,实现分类搜索，同类型文章推荐，登陆，注册，评论，点赞，留言，统计等。',
          url: 'http://yangzhiping.site/'
        },
        {
          title: '个人简历（2018版） 媒体查询',
          des:
            '采用@media + rem + animate.css + wow.js + jQuery + font-awesome, 增加动画效果，让简历更美观。',
          url: 'http://gresume.yangzhiping.site/'
        },
        {
          title: '个人简历（2019版） Vue',
          des: 'Vue + sass + vw,vh进行适配，让简历能够在移动端上显示。',
          url: 'https://junquan-guo.github.io/'
        },
        {
          title: '模块管理打包工具',
          des: 'webpack | gulp | grunt 等模块管理打包工具的学习和使用。',
          url: 'https://gitee.com/ceartmy/Build'
        },
        {
          title: '小程序合集',
          des: '针对小程序提升，进行模块化的学习、对知识进行查漏补缺。',
          url: 'https://gitee.com/ceartmy/applet'
        },
        {
          title: '高校新闻（2017版）asp.net',
          des: 'asp.net + SQLserver + jQuery + iconfont字体图标，登陆、注册、搜索、文章排序。',
          url: 'https://github.com/Junquan-Guo/news'
        }
      ],
      viewMore:{
        title:'github上面查看更多',
        url:'https://github.com/Junquan-Guo/'
      },
      presentId: 0,//当前页
      finally: 5,//最后一页
      lateX:0,
      lateZ:0, 
      scale:1
    };
  },
  created(){
    let _this = this;
    _this.finally=this.worksList.length
  }
  ,
  methods: {
    previousPage(presentId) {
      if(presentId==0)
        return ;
      this.presentId=presentId-1
    },  
    nextPage(presentId) {
      if(presentId==this.finally-1)
        return ;
      this.presentId=presentId+1
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
.work 
  background: #4b85a0

  .content 
    position: absolute
    top: 15vh
    left: 10vw
    right: 10vw

    .work-list 
      transform-style: preserve-3d
      width: 18.75rem
      padding: 0
      height: 60vh
      transition: transform 2s
      display: flex
      justify-content: space-between
      margin: 0 auto
      color: #000

      .work-list-item 
        box-shadow: 0 0.3125rem 0.625rem rgba(0,0,0,.2)
        box-sizing: border-box
        border-radius: .375rem
        padding: .625rem
        height: 60vh
        position: absolute
        text-align: justify
        transition: transform .5s
        background: hsla(0,0%,100%,.98)

        .-title 
          margin: 1.5625rem 0
          text-align: center

          .-link 
            color: #4985a0

        .-des 
          line-height: 1.25rem
          font-size: .875rem
        
        .-qrcode 
          display: flex
          flex-direction: column
          align-items: center

          .-img 
            width: 6.25rem
            height: 6.25rem

          .-des 
            line-height: 1.25rem
            font-size: .875rem
        
        .work-link 
          display: flex
          flex-direction: column
          align-items: center
          border-radius: .125rem
          cursor: pointer
          width: 9.375rem
          margin: 3.125rem auto 0

          .-img 
            width: 9.375rem
            height: 2.5rem
            border: 1px solid #999
            background: url(../assets/images/w_link.svg) 50% no-repeat
            background-size: 50% 50%

            .-des 
              line-height: 1.25rem
              font-size: .875rem

    .more 
      text-align: center
      padding-top: 1.5625rem

      a 
        text-decoration: underline

    .switch 
      padding: 1.5625rem 0
      width: 15.625rem
      margin: 0 auto
      height: 1.875rem
      z-index: 1
      display: flex
      justify-content: space-between

      .left,.right  
        border-radius: 50%
        border: 1px solid #fff
        height: 1.875rem
        width: 1.875rem
        position: relative
        cursor: pointer
        background: url(../assets/images/arrow.svg) center 35% no-repeat;
        background-size: 70%
        transform: rotate(-90deg)

      .right 
        transform: rotate(90deg)

</style>
