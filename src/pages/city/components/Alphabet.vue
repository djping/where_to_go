<template>
  <div class="list">
    <ul>
      <li class="item"
        v-for="(item,key) of alphabet"
        :ref="key"
        @click="handleLetterClick"
        @touchstart = "handleTouchStart"
        @touchmove = "handleTouchMove"
        @touchend = "handleTouchEnd"
      >{{key}}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'CityAlphabet',
  props:{
    alphabet:Object
  },
  computed: {
    letters () {
      let letters = []
      for (let i  in this.alphabet) {
        letters.push(i)
      }
      return letters
    }
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change',e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          let touchY = e.touches[0].clientY - 80
          let index = Math.floor((touchY - this.startY) / 15)
          console.log(index)
          if (index >= 0 && index < this.letters.length) {
           this.$emit('change',this.letters[index])
          }
        },20)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  },
  data () {
    return {
      touchStatus: false,
      startY:0,
      timer:null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  }
}
</script>
<style lang="stylus" scoped>
  .list
    position absolute
    top 1.8rem
    bottom 0
    right 0
    width .4rem
    display flex
    flex-direction column
    justify-content center
    .item
      color #00bcd4
      line-height .3rem
</style>
