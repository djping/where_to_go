<template>
  <div class="list">
    <div v-for="item of categoryList">
      <div class="title border-bottom">
        <span class="icon"></span>
        <span class="decs">{{item.title}}</span>
      </div>
      <div class="child" v-if="item.children">
          <detail-list :categoryList="item.children">
          </detail-list>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'DetailList',
  props: {
    categoryList: Array
  }
}
</script>
<style lang="stylus" scoped>
  .list
    .title
      line-height .15rem
      font-size: .32rem;
      padding .15rem
      width 100%
      text-align left
      .icon
        display: inline-block;
        position: relative
        top: .06rem
        left: .06rem
        width: .36rem;
        height: .36rem;
        background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat;
        margin-right: .1rem;
        background-size: .4rem 3rem;
    .child
      padding 0 .3rem
</style>