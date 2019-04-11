<template>
  <div class="header">
    <div class="iconfont">
      <router-link to="/">
        <span class="back">&#xe600;</span>
      </router-link>
      <span class="title">城市选择</span>
    </div>
  </div>
</template>
<script>
export default {
  name: 'CityHeader'
}
</script>
<style lang="stylus" scoped>
  .header
    width 100%
    height .8rem
    background #00bcd4
    color #fff
    margin-top -1.2rem
    display flex
    .back
      text-align left
      position absolute
      left .3rem
      top .2rem
      font-size .2rem
      color #fff
    .title
      position absolute
      top .2rem
      left 50%
      transform translate(-50%,0)
</style>
