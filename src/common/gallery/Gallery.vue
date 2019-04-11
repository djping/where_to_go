<template>
  <div class="gallery" @click="handleGalleryClick">
    <div class="wrapper">
     <swiper :options="swiperOption">
      <swiper-slide v-for="item of imgs">
        <img class="gallery-img" :src="item">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
    </div>
  </div>
</template>
<script>
export default {
  name: 'CommonGallery',
  props: {
    imgs: {
      type: Array
    }
  },
  methods: {
    handleGalleryClick () {
      this.$emit('change')
    }
  },
  data () {
    return {
      swiperOption : {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        //自我刷新 --gallery不动的情况
        observer: true,
        observeParents: true
      }
    }
  }
}
</script>
<style lang="stylus" scoped>
  .gallery >>> .swiper-container
    overflow inherit
  .gallery
    position absolute
    top 0
    right 0
    left 0
    bottom 0
    background black
    .wrapper
      width 100%
      height 50%
      position absolute
      top 50%
      transform translate(0,-50%)
      background #fff
      .gallery-img
        width 100%
    .swiper-pagination
      color #fff
      bottom -.8rem
      z-index 99
</style>