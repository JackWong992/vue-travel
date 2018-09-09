<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list :cities="cities" 
               :hot="hotCities"
               :letter="letter">
    </city-list >
    <city-alphabet :cities="cities" 
        @change="handleLetterChange"></city-alphabet>
  </div>
</template>

<script>
  import CityHeader from "./components/Header.vue"
  import CitySearch from "./components/Search.vue"
  import CityList from "./components/List.vue"
  import CityAlphabet from "./components/Alphabet.vue"
  import axios from 'axios'
  export default {
    name: 'City',
    components: {
      CityHeader:CityHeader,
      CitySearch:CitySearch,
      CityList: CityList,
      CityAlphabet: CityAlphabet
    },
    data() {
      return {
        cities: {},
        hotCities: [],
        letter: ''
      }
    },
    methods: {
      getCityInfo(){   //   /api/city.json
        axios.get('https://www.easy-mock.com/mock/5b94e84ddd236325f85bf87a/travel/city').then(this.handleGetCityInfoSucc)
      },
      handleGetCityInfoSucc(res){
        res = res.data
        if( res.ret  && res.data ){
          const data = res.data 
          this.cities = data.cities
          this.hotCities = data.hotCities
          console.log(res)
        }
      },
      handleLetterChange(letter){
        this.letter = letter
        console.log('父组件'+letter)
      }
    },
  mounted(){
    this.getCityInfo()
  }
}
</script>

<style scoped>

</style>