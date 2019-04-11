<template>
  <div>
    <div class="search">
      <input v-model="keyword" type="text" placeholder="输入城市或拼音">
    </div>
    <div class="search-content" v-show="keyword">
      <ul>
        <li class="item border-bottom" 
            v-for="item of list"
            @click="handleCityClick(item.name)"
        >
          {{item.name}}
        </li>
        <li class="item" v-show="!list.length">没有找到数据</li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: 'CitySearch',
  props:{
    cities:Object
  },
  data () {
    return {
        keyword:'',
        list:[],
        timer:null
    }
  },
  methods: {
    handleCityClick (city) {
      this.$store.commit('changeCityState',city)
      this.$router.push('/')
    }
  },
  watch: {
    keyword () {
      console.log(this.keyword)
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        const result = []
        for(let i in this.cities) {
          this.cities[i].forEach((value) => {
           if (this.keyword !== '') {
              if (value.name.indexOf(this.keyword) !== -1 ||
                  value.spell.indexOf(this.keyword) !== -1
               ) {
                result.push(value)
              }
           }
            /*if (value.name.indexOf(this.keyword) !== -1 ||
                  value.spell.indexOf(this.keyword) !== -1
               ) {
              result.push(value)
            }*/
          })
        }
        this.list = result
      },100)
    }
  }
}
</script>
<style lang="stylus" scoped>
.search
  width 100%
  height .8rem
  background #00bcd4
  padding .1rem
  input
    box-size border-box
    padding .1rem
    width 8rem
    height .6rem
    border-radius .1rem
    text-align center
    color #666
.search-content
  position absolute
  top 1.8rem
  left 0
  right 0
  bottom 0
  background #eee
  z-index 1
  .item
    line-height .4rem
    text-align left
    text-indent .2rem
    background white
    padding .2rem
</style>
