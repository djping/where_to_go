<template>
  <div class="header">
    <router-link to="/" tag="div" 
      class="back" v-show="toggle">
      <span class="iconfont btn">&#xe600;</span>
    </router-link>
    <div class="header-info" 
      v-show="!toggle"
      :style="opacityStyle"
      >
      <router-link to="/" tag="div"
        class="iconfont">&#xe600;</router-link>
      <div class="title">景点详情</div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      toggle: true,
      opacityStyle: {
        opacity:0
      }
    }
  },
  methods: {
    handleScroll() {
      const top = document.documentElement.scrollTop
      console.log(document.documentElement.scrollTop)
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {opacity}
        this.toggle = false
      }else {
        this.toggle = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll',this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll',this.handleScroll)
  }
}
</script>
<style lang="stylus" scoped>
  .header
    position relative
    margin-top 3.5rem
    .back
      position absolute
      top -4.5rem
      height .6rem
      width .6rem
      border-radius .3rem
      color #fff
      background black
      text-align center
      z-index 999
      .btn
        position absolute
        top .1rem
        left 5px
        font-size .2rem
    .header-info
      width 2rem
      z-index 9
      display flex
      justify-content space-between
      width 100%
      height .6rem
      background #00afc7
      position fixed
      top 0rem
      line-height .6rem
      padding .2rem
      .header-back
        width 1rem
      .title
        flex 1
        color #fff
        font-size .3rem
</style>