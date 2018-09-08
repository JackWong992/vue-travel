<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" src="http://img1.qunarzz.com/sight/p0/1609/80/8092254b7f5f016ea3.water.jpg_600x330_45017f19.jpg">
      <div class="banner-info">
        <div class="banner-title">大连海洋景区5A级别国家景区</div>
        <div class="banner-number" >
        <span class="iconfont icon-tupian"></span> 39
        </div>
      </div>
    </div>
    <common-gallary :imgs="imgs" v-show="showGallary"
    @close="handleGallaryClose"></common-gallary>
  </div>
</template>

<script>
  import CommonGallary from  'common/gallary/Gallary.vue'
  export default {
    name: 'DetailBanner',
    data() {
      return {
        showGallary: false,
        imgs: ['http://img1.qunarzz.com/sight/p0/1709/fb/fb5f50e934a895bea3.water.jpg_r_800x800_30584971.jpg','http://img1.qunarzz.com/sight/p0/1703/22/2244eaab209bf750a3.img.jpg_r_800x800_d4d9e847.jpg','http://img1.qunarzz.com/sight/p0/1704/74/74a3ba6334dd7cfa3.img.jpg_r_800x800_c2612186.jpg']
      }
    },
    components: {
      CommonGallary: CommonGallary
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