<template>
  <div class="header">
    <div class="header-left">left</div>
    <div class="header-input">输入城市\景点\目的地</div>
    <div class="header-right">right</div>
  </div>
</template>
<script>
export default {
  name: 'HomeHeader'
}
</script>
<style lang="stylus" scoped>
.header
  margin-top -60px
  font-size 25px
  line-height 86px
  color #fff
  width 100%
  height 86px
  display flex 
  background #00bcd4
  .header-left
    width 80px
  .header-input
    height 60px
    flex 1
    border-radius 5px
    margin 10px 0
    margin-left 2px
    background #fff
    color #ccc
    line-height 60px
    text-align left
  .header-right
    width 120px
    text-align center
</style>
