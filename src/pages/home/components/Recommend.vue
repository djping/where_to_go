<template>
  <div>
    <p class="title">热门推荐</p>
    <ul>
      <router-link :to="'/detail/' + item.id" tag="li"
        class="item border-bottom" 
        v-for="(item,index) of list"
      >
        <div class="item-img-wrapper">
          <img :src="item.imgUrl" />
        </div>
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">了解详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>
<script>
export default {
  name:"HomeRecommend",
  props:{
    list: Array
  }
}
</script>
<style lang="stylus" scoped>
  .title
    height 1rem
    background #eee
    font-size .45rem
    line-height 1rem
    text-indent .3rem
    text-align left
    margin-top .2rem
 
  .item
    position relative
    height 0
    margin-bottom .2rem
    padding-bottom 2rem
    .item-img-wrapper
      float left
      width 25%
      height 2rem
      img
        height 100%
        width 100%
    .item-info
      float left
      height 2rem
      overflow hidden
/*      white-space nowrap
      text-overflow ellipsis
      margin-bottom 10px*/
      .item-title
        font-size .32rem
        line-height 1rem
        text-align left
        text-indent .2rem
        color #212121
        font-family Arial
      .item-desc
        font-size .24rem
        text-indent .2rem
        color #f55
      .item-button
        position absolute
        right .2rem
        bottom .2rem
        background #ff8300
        border-radius .1rem
        font-size .2rem
</style>