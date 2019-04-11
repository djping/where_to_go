<template>
  <div class="header">
    <div><span class="iconfont back">&#xe600;</span></div>
    <div class="header-input">
      <span class="iconfont serach">&#xe601;输入城市\景点\目的地
      </span>
    </div>
  <router-link to="/city">
    <div class="header-right">
      <span 
      class="iconfont city">
      {{this.$store.state.city}}&#xe607;</span>
    </div>
  </router-link>
  </div>
</template>
<script>
export default {
  name: 'HomeHeader',
}
</script>
<style lang="stylus" scoped>
  @import '~@/assets/styles/varibles.styl'

  .header
    margin-top -1.2rem
    height 1.2rem
    font-size .4rem
    display flex
    background $bgColor
    color #fff
    line-height 1.4rem
    text-align center
    .back
      font-size .2rem
      position relative
      top -.2rem
    .header-left
      width 1rem
      margin-left -.4rem
    .header-input
      .serach
        font-size .35rem
        position relative
        top -.2rem
        padding .1rem
      flex 1
      padding-left .4rem
      margin .2rem
      border-radius .1rem
      background #fff
      color #ccc
      text-align left
      line-height 1.3rem
    .header-right
      width 2rem
      color #fff
      .city
        font-size .2rem
        position relative
        top -.18rem
        font-size .4rem
</style>
