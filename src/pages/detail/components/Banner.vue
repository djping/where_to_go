<template>
  <div>
    <div class="banner" 
      @click="handleBannerClick"
    >
      <img class="banner-img" :src="bannerImg" />
      <div class="banner-info">
        <div class="banner-des">{{sightName}}</div>
        <div class="banner-number">
          <span class="iconfont">&#xe602;999</span></div>
      </div>
    </div>
    <fade-animation>
      <common-gallery 
      :imgs="gallaryImgs"
      v-show="showGallery"
      @change="handleBannerClick"
      ></common-gallery>
    </fade-animation>
  </div>
</template>
<script>
import CommonGallery from '@/common/gallery/Gallery'
import FadeAnimation from '@/common/fade/FadeAnimation'

export default {
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  components: {
    CommonGallery,
    FadeAnimation
  },
  methods: {
    handleBannerClick () {
      this.showGallery = !this.showGallery
      this.$emit('change')
    }
  },
  data () {
    return {
      imgLists: [],
      showGallery: false
    }
  }
}
</script>
<style lang="stylus" scoped>
  .banner
    position absolute
    top -.8rem
    overflow hidden
    height 0
    padding-bottom 55%
    .banner-img
      width 100%
    .banner-info
      position absolute
      left 0
      right 0
      bottom  0
      padding .2rem
      color #fff
      font-size .36rem
      font-family sans-serif
      display flex
      background-image linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
      .banner-des
        flex 1
        text-align left
      .banner-number
        height .4rem
        line-height .4rem
</style>