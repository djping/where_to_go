<template>
  <div class="icons">
    <swiper :options="swiperOption"
     v-if="iconLists.length">
      <swiper-slide v-for="(page,index) of pages">
        <div class="icon" v-for="(item,index) of page">
          <div class="icon-img">
            <img class="img-content" :src="item.imgUrl">
            <p class="icon-des">{{item.title}}</p>
          </div>
        </div>
        </swiper-slide>
      </swiper>
    </div>
<!--     <div class="icon" v-for="item of iconLists">
      <div class="icon-img">
        <img class="img-content" :src="item.imgUrl">
        <p class="icon-des">{{item.des}}</p>
      </div>
    </div> -->
  </div>
</template>
<script>
export default {
  name:"HomeIcons",
  props:{
    iconLists: Array
  },
  data () {
    return {
      swiperOption: {
        loop:true,
        autoplay:false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconLists.forEach((item,index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import '~@/assets/styles/mixins.styl'

    .icons >>> .swiper-container
      height 0
      padding-bottom 50%
    .icon
      position relative
      float left
      width 25%
      height 0
      padding-bottom 25%
      .icon-img
        min-width 0
        position absolute
        bottom .44rem
        top 0
        left 0
        right 0
        .img-content
          height 100%
        .icon-des
          color #333
          line-height .44rem
          font-size .4rem
          // ellipsis()
          overflow hidden
          white-space nowrap
          text-overflow ellipsis
</style>