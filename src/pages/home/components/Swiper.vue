<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img :src="item.imgUrl" class="swiper-img">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "HomeSwiper",
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      swiperList: [{
        id: "001",
        imgUrl: "http://img1.qunarzz.com/piao/fusion/1805/e5/59fad13a64807d02.jpg_750x200_713ae984.jpg"
      },{
        id: "002",
        imgUrl: "http://img1.qunarzz.com/piao/fusion/1808/8a/1957a0fb58ad0402.jpg_750x200_e72b8c0f.jpg"
      }]
    };
  }
};
</script>

<style scoped lang="stylus">
  .wrapper>>>.swiper-pagination-bullet
    background: #fff!important
  .wrapper
    width: 100%
    height: 0
    overflow: hidden
    padding-bottom: 26.5%
    .swiper-img 
      width: 100%
      
</style>