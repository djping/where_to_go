<template>
  <div>
    <detail-banner 
      @change="show"
      :sightName="sightName"
      :bannerImg="bannerImg"
      :gallaryImgs="gallaryImgs"
    ></detail-banner>
    <detail-header v-show="showBanner"></detail-header>
    <div class="content" v-show="showBanner">
      <detail-list 
      :categoryList="categoryList"
      ></detail-list>
    </div>
  </div>
</template>
<script>
import axios from 'axios'

import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data () {
    return {
     showBanner: true,
     sightName: '',
     bannerImg: '',
     gallaryImgs: [],
     categoryList: []
    }
  },
  methods: {
    show () {
      this.showBanner = !this.showBanner
      console.log(222)
    },
    getInfo () {
      axios.get('./mock/detail.json',{
        params: {
          id: this.$route.params.id
        }
      })
          .then(this.distributeData)
    },
    distributeData (res) {
      let data = res.data
      if (data.ret) {
        this.sightName = data.data.sightName
        this.bannerImg = data.data.bannerImg
        this.gallaryImgs = data.data.gallaryImgs
        this.categoryList = data.data.categoryList
        console.log(this.sightName)
      }
    }
  },
  mounted () {
    this.getInfo()
  }
}
</script>
<style lang="stylus" scoped>
  .content
    height 20rem
</style>