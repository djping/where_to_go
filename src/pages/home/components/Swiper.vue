<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="item of list" 
                    :key="item.id">
        <img class="swiper-img" :src="item.imgUrl">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>
<script>
export default {
  name: 'HomeSwiper',
  props:{
    list:Array
  },
  data () {
    return {
      swiperOption: {
        pagination:'.swiper-pagination',
        loop:true
      }
    }
  }
}
</script>
<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet-active
    background: white !important
  .wrapper
    width 100%
    overflow hidden
    height 0
    padding-bottom 31.2%
    .swiper-img
      width:100%
</style>
