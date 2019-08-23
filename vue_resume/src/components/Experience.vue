<template>
  <!-- 经历 -->
  <section class="experience fp-section" style="">
    <div class="content">
      <div class="slider" style="transform: rotateY(0deg) rotateX(0deg);">
        <div class="slider-container" v-for="(list,index) in experience" :key="index" v-if="index===selected">
          <div class="left">
            <div class="img" :style="list.logo"></div>
            <h4>{{list.title}}</h4>
            <p class="-post">"<span>{{list.post}}</span>"</p>
          </div>
          <div class="right">
            <p class="-time">{{list.time}}</p>
            <ul class="-list">
              <li class="exp-item" v-for="item in list.contentList">{{item}}</li>
            </ul>
          </div>
        </div>
      </div>
      <div class="shout-cut">
        <ul>
          <li v-for="(list,index) in experience"  :key="index" :class="{active:index==selected}" @click="btn(index)"></li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Experience',
  data () {
    return {
      selected: 0,
      lastPosX: 0,
      lastPosY: 0,
      curPosX: 0,
      curPosY: 0,
      experience:[
          {
            logo:{
              backgroundImage:'url('+require('../assets/images/logo_jm.jpg')+')'
            },
            title: '炘楠文化传播（广州）',
            post: '前端工程师/网站维护',
            time: '2018年7月~至今',
            contentList: ['应用HTML、CSS、JS、JQ等前端技术快速构建高质量代码；', '及时响应上级提出的问题并快速处理线上产品出现的bug', '了解实用技术用以提升产品的交换效果，使管理员操作更加人性化', '前端页面实现和数据绑定，测试，维护，后台数据库查询，连接']
          },
          {
            logo:{
              backgroundImage:'url('+require('../assets/images/logo_lt.png')+')'
            },
            title: '广东工贸职业技术学院',
            post: '软件技术专业',
            time: '2016年9月~2019年6月',
            contentList: ['2018学年：获得学校三好学生（三等奖学金）。', '班级排名：4/54', '主修课程：Java,php,python，html5,Android,ios等', '2017.09  网信部成员，公众号编辑，微博等平台运营。']
          }
      ]
    }
  },
  methods: {
    btn(index) {
      this.selected=index
    } 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
.experience 
  background: #945c4c

  .content 
    position: absolute
    top: 15vh
    left: 0
    right: 0
    perspective: 93.75rem

    .slider 
      width: 80vw
      height: 55vh
      background: #f2f4f5
      margin: 0 auto
      padding: 0 5vw
      border-radius: .3125rem
      color: #000
      transition: transform .3s linear
      overflow: hidden
      box-shadow: 0 0 0.78125rem rgba(0,0,0,.5)
      border: 1px solid #eee
      display: flex
      justify-content: center

      .slider-container 
        transition: opacity .3s

        .img 
          background: 50% no-repeat
          background-size: contain
          width: 12.5rem
          height: 3.125rem
          margin: 1.5625rem auto 0

        h4 
          color: #945c4c
          font-size: 1rem
          text-align: center
          margin-bottom: .625rem

        .-post 
          color: #9e6351
          font-size: .8125rem
          margin: 0 auto 1.5625rem
          text-align: center
        
        .-time 
          color: #af7464
          font-size: .8125rem
        
        .-list 
        
          .exp-item 
            font-size: .75rem
            line-height: 1rem
            margin: .375rem 0
            position: relative

            &:before 
              content: ""
              position: absolute
              top: 50%
              left: -3vw
              width: .3125rem
              height: .3125rem
              transform: translateY(-50%)
              border-radius: 50%
              background-color: #af7464
    
    .shout-cut 
      width: 50vw
      margin: 0 auto
      padding-top: 15vh

      ul 
        display: flex
        justify-content: space-between
        align-items: center
        z-index: 101

        li 
          width: .625rem
          height: .625rem
          border-radius: 50%
          background-color: #623c32
          cursor: pointer
          transition: background-color .3s linear
          position: relative

        .active
          background-color: #af7164
          
</style>
