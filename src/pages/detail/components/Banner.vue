<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg">
      <div class="banner-info">
        <div class="banner-title">{{sightName}}</div>
        <div class="banner-number" >
        <span class="iconfont icon-tupian"></span> {{this.bannerImgs.length}}
        </div>
      </div>
    </div>
    <fade-animation>
      <common-gallary :imgs="bannerImgs" v-show="showGallary"
      @close="handleGallaryClose"></common-gallary>
    </fade-animation>  
  </div>
</template>

<script>
  import CommonGallary from  'common/gallary/Gallary.vue'
  import FadeAnimation from 'common/fade/FadeAnimation.vue'
  export default {
    name: 'DetailBanner',
    props: {
      sightName: String,
      bannerImg: String,
      bannerImgs: Array
    },
    data() {
      return {
        showGallary: false
      }
    },
    components: {
      CommonGallary: CommonGallary,
      FadeAnimation: FadeAnimation
    },
    methods: {
      handleBannerClick(){
        this.showGallary = true
      },
      handleGallaryClose(){
        this.showGallary = false
      }
    }
  }
</script>

<style scoped lang="stylus">
  .banner
    position: relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-info
      position: absolute
      left: 0
      right: 0
      bottom: 0
      color: #ffa631
      line-height: .6rem
      background: #ccc
      opacity: .9
      display: flex
      justify-content: space-between
      .banner-title
        text-indent: .2rem
        font-size: .32rem
      .banner-number
        border-radius: .2rem
        height: .45rem
        line-height: .45rem
        background: rgba(0,0,0,.3)
        padding: 0 .2rem 
        margin-top: .07rem
        margin-right: .3rem  
        color: #fff
</style>