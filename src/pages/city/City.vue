<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list 
      :hotCities="hotCities" 
      :cities="cities"
      :letter="letter"
      ></city-list>
    <city-alphabet 
      :alphabet="alphabet"
      @change="handleLetterChange"
      ></city-alphabet> 
  </div>
</template>
<script>
import axios from 'axios'

import CityHeader from "./components/Header"
import CitySearch from "./components/Search"
import CityList from "./components/List"
import CityAlphabet from "./components/Alphabet"

export default {
  name: 'City',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      hotCities: [],
      cities: {},
      alphabet: {},
      letter: ''
    }
  },
  methods: {
    getCityInfo () {
      axios.get('./mock/city.json')
        .then(this.getDetailInfo)
    },
    getDetailInfo (res) {
      console.log(res.data)
      let data = res.data
      this.hotCities = data.data.hotCities
      this.cities = data.data.cities
      this.alphabet = this.cities
      console.log(this.cities)
    },
    handleLetterChange (key) {
      this.letter = key
    }
  },
  mounted () {
    this.getCityInfo()
  }
}
</script>
<style lang="stylus" scoped></style>
