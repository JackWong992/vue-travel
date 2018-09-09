<template>
  <div>
    <detail-banner
    :sightName="sightName"
    :bannerImg="bannerImg"
    :bannerImgs="gallaryImgs"></detail-banner>
    <detail-header></detail-header>
    <div class="content">
      <detail-list :list="list"></detail-list>
      <detail-recommend></detail-recommend>
    </div>
  </div>
</template>

<script>
 import DetailBanner from './components/Banner.vue'
 import DetailHeader from './components/Header.vue'
 import DetailList from './components/List.vue'
 import DetailRecommend from './components/Recommend.vue'
 import axios from 'axios'
  export default {
    name: 'Detail',
    components: {
      DetailBanner: DetailBanner,
      DetailHeader: DetailHeader,
      DetailList: DetailList,
      DetailRecommend: DetailRecommend
    },
    data() {
      return {
        sightName: '',
        bannerImg: '',
        gallaryImgs: [],
        list: [] 
      }
    },
    
    methods: {
      getDetailInfo () {
        axios.get('https://www.easy-mock.com/mock/5b94e84ddd236325f85bf87a/travel/detail', {
          params: {
            id: this.$route.params.id
          }
        }).then(this.handleGetDataSucc)
    },
    handleGetDataSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.sightName = data.sightName
        this.bannerImg = data.bannerImg
        this.gallaryImgs = data.gallaryImgs
        this.list = data.categoryList
        console.log(res)
      }
    }
  },
  mounted () {
    this.getDetailInfo()
  }
  }
</script>

<style scoped lang="stylus">
  .content
    height: 15.5rem
</style>