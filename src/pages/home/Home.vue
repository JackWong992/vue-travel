<template>
  <div>
    <home-header></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icon :list="iconList"></home-icon>
    <home-recommend :list="recommendList"></home-recommend>
    <home-weekend :list="weekendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from "./components/Header.vue"
import HomeSwiper from "./components/Swiper.vue"
import HomeIcon from "./components/Icon.vue"
import HomeRecommend from "./components/Recommend.vue"
import HomeWeekend from "./components/Weekend.vue"
import axios from "axios"
import {mapState} from 'vuex'

export default {
  name: "Home",
  components: {
    HomeHeader: HomeHeader,
    HomeSwiper: HomeSwiper,
    HomeIcon: HomeIcon,
    HomeRecommend: HomeRecommend,
    HomeWeekend: HomeWeekend
  },
  data(){
    return {
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: [],
      lastCity: ''
    }
  },
  methods: {
    getHomeInfo(){
      axios.get('https://www.easy-mock.com/mock/5b94e84ddd236325f85bf87a/travel/index?city='+this.city)
       .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc(res){
      console.log(res)
      res = res.data
      if( res.ret  && res.data ){
        const data = res.data 
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.recommendList = data.recommendList
        this.weekendList = data.weekendList
      }
    }
  },
  computed: {
    ...mapState(['city'])
  },
  mounted(){
    this.lastCity = this.city
    this.getHomeInfo()
  }
};
</script>

<style scoped>
</style>