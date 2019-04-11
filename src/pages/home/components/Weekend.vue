<template>
  <div>
    <p class="title">周末去哪儿</p>
    <ul>
      <li class="item border-bottom"
        v-for="item of list">
        <div class="item-img-wrapper">
          <img :src="item.imgUrl" />
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name:"HomeWeekend",
  props: {
    list:Array
  }
}
</script>
<style lang="stylus" scoped>
  .title
    height 1rem
    background #eee
    font-size .4rem
    color #212121
    line-height 1rem
    text-indent .3rem
    text-align left
    margin-top .2rem
  .item
    item-img-wrapper
      mergin-bottom .2rem
      overflow hidden
      height 0
      padding-bottom 28.09%
    .item-info
      padding .2rem
      .item-title
        color #212121
        font-size .28rem
        line-height .28rem
        text-align left
        text-indent .2rem
        margin-bottom .13rem
      .item-desc
        color #616161
        font-size .24rem
        line-height .24rem
        text-align left
        text-indent .2rem
        margin-bottom .13rem
</style>
