<template>
  <div class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page,index) in pages" :key="index">
          <div class="icon" v-for="item in page"  :key="item.id">
            <div class="icon-img" >
              <img :src="item.imgUrl" class="icon-img-content">  
            </div>
            <p class="icon-desc">{{item.desc}}</p>
          </div>
      </swiper-slide>
      
    </swiper>   
  </div>
</template>

<script>
export default {
  name: "HomeIcon",
  props: {
    list: Array
  },
  data() {
    return {
       swiperOption: {
         autoplay: false
      }
    }
  },
  computed:{
    pages(){
      const pages = []
      this.list.forEach( (item,index)=>{
        const page = Math.floor(index/8) //数据的下标大于7的时候page=1
        if( !pages[page] ){
          pages[page]=[]
        }
        pages[page].push( item )
      })
      return pages
    }
  }
};
</script>

<style scoped lang="stylus">
@import '~@/assets/styles/varibles.styl';
.icons >>> .swiper-container
  height: 0
  padding-bottom: 50% 
.icon 
  height: 0
  overflow: hidden
  position: relative
  width: 25%
  float: left
  padding-bottom: 25%
  .icon-img 
    position: absolute
    top: 0
    left: 0
    right: 0
    bottom: 0.44rem
    .icon-img-content 
      height: 100%
      display: block
      margin: 0 auto
.icon-desc 
  position: absolute
  left: 0
  right: 0
  bottom: 0
  line-height: 0.44rem
  color: $darkTextColor
  height: 0.44rem
  text-align: center
</style>