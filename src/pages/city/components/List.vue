<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
       <div class="title border-topbottom">当前位置</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.$store.state.city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" 
            v-for="item of hotCities">
            <div 
              class="button"
              @click="handleCityClick(item.name)"
            >
              {{item.name}}
            </div>
          </div>
        </div>
      </div>
      <div class="area"
          v-for="(item,key) of cities"
          :ref="key"
      >
        <div class="title border-topbottom">{{key}}</div>
        <div class="city-list">
          <div class="city border-topbottom"
               v-for="cityArr of item"
               @click="handleCityClick(cityArr.name)"
          >
            {{cityArr.name}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Bscroll from "better-scroll"

export default {
  name: 'CityList',
  props: {
    hotCities:Array,
    cities:Object,
    letter:String
  },
  methods: {
    handleCityClick (city) {
      this.$store.dispatch("changeCity",city)
      this.$router.push('/')
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch:{
    letter () {
      let clicked = this.letter
      this.scroll.scrollToElement(this.$refs[clicked][0])
    }
  }
}
</script>
<style lang="stylus" scoped>
  .border-topbottom
    &:before 
      border-color #ccc
    &:after 
      border-color #ccc
  .list
    overflow hidden
    position absolute
    top 1.8rem
    left 0
    right 0
    bottom 0
    text-align left
    .title
      line-height .4rem
      background #eee
      font-size .24rem
      padding .1rem
    .button-list
      width 100%
      display flex
      flex-wrap wrap
      .button-wrapper
        padding .15rem
        width 27%
        .button
          padding .1rem
          border .02rem solid #00bcd4
          border-radius .1rem
          text-align center
    .city-list
      .city
        padding .15rem
        line-height .4rem
</style>
