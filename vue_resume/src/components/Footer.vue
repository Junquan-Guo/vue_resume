<template>
  <!-- footer -->
  <footer style="display: block;">
    <div class="github">
      <iframe
        src="https://ghbtns.com/github-btn.html?user=Junquan-Guo&amp;repo=resume&amp;type=star&amp;count=true&amp;size=small"
        frameborder="0"
        scrolling="0"
      ></iframe>
      <iframe
        src="https://ghbtns.com/github-btn.html?user=Junquan-Guo&amp;repo=resume&amp;type=fork&amp;count=true&amp;size=small"
        frameborder="0"
        scrolling="0"
      ></iframe>
    </div>
    <p v-for="item in system">{{item.sys}}</p>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      system:[
        {sys:'Released under the MIT License'},
        {sys:'All Rights Reserved'},
        {sys:'Copyright © 2014-2019 Korey Zhao'}
      ]
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
footer 
  z-index: 11
  bottom: 0
  left: 0
  right: 0
  position: absolute
  font-size: .625rem
  line-height: .5rem
  border-top: 1px solid #756d4d
  text-align: center
  color: #756d4d

  .github 
    margin: .625rem auto 0
    width: 2.5rem
    height: 1.5625rem
    display: flex
    justify-content: space-around

    iframe 
      width: 5.15625rem
    

</style>
