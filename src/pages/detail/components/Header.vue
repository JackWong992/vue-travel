<template>
  <div>
    <router-link to="/" tag="div" class="header-abs" v-show="showAbs">
        <span class="iconfont icon-fanhui"></span>
    </router-link>
    <div class="header-fixed" v-show="!showAbs"
    :style="opacityStyle">
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe624;</div>        
      </router-link>
      景点详情</div>
  </div>
</template>

<script>
  export default {
    name: 'DetailHeader',
    data() {
      return {
        showAbs: true,
        opacityStyle: {
          opacity: 0
        }
      }
    },
    methods: {
      handleScroll(){
        console.log('deactivated...')
        const top = document.documentElement.scrollTop
        if (top > 60) {
          let opacity = top / 140
          opacity = opacity > 1 ? 1 : opacity
          this.opacityStyle = { opacity }
          this.showAbs = false
         } else {
          this.showAbs = true
        }
      }
  },
  mounted () {
    window.addEventListener( 'scroll', this.handleScroll )
  },
  deactivated(){
    window.removeEventListener( 'scroll', this.handleScroll )    
  }
}
</script>

<style scoped lang="stylus">
  @import '~@/assets/styles/varibles.styl'
  .header-abs
    position: absolute
    left: .2rem
    top: .2rem
    width: .8rem
    height: .8rem
    border-radius: .4rem
    background: rgba(0,0,0,.8)
    text-align: center
    .icon-fanhui
      color: #fff
      height: .8rem
      line-height: .8rem
  .header-fixed
    position: fixed
    top: 0
    left: 0
    right: 0
    height: .86rem
    line-height: .86rem
    text-align: center
    background: $bgColor
    color: #fff
    font-size: .32rem
    .header-fixed-back
      position: absolute
      top: 0
      left: 0
      width: .64rem
      text-align: center
      font-size: .4rem
      color: #fff
</style>