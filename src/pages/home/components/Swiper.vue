<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="list.length">
      <swiper-slide v-for="item of list" :key="item.id">
        <img :src="item.imgUrl" class="swiper-img">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "HomeSwiper",
  props: {
    list: Array
  },
  data() {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
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
    padding-bottom: 27%
    .swiper-img 
      width: 100%
      
</style>