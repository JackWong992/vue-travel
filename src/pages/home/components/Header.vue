<template>
  <div>
    <div class="header">
      <div class="header-left">
        <span class="iconfont icon-fanhui"></span> 
      </div>
      <div class="header-input">
        <span class="iconfont icon-xiaoxi-"></span>
        输入城市/景点/游玩主题
      </div>
      <router-link to="/City">
        <div class="header-right">
        {{this.$store.state.city}}<span class="iconfont icon-jiantouxia"></span>
        </div>
      </router-link>
      
    </div>
  </div>
</template>

<script>
  export default {
    name: 'HomeHeader',
    props: {
      city: String
    }
  }
</script>

<style scoped lang="stylus">
  @import "~@/assets/styles/varibles.styl";
  .header
    display: flex
    line-height: .86rem
    background: $bgColor
    color: #fff
    .header-left
      width: .64rem
      float: left
      text-align: center
    .header-input
      flex:1
      height: .64rem
      border-radius: .1rem
      background: #fff
      margin-left: .2rem
      margin-top: .12rem
      margin-bottom: .1rem
      color: #ccc
      line-height: .64rem
      padding-left: .1rem
    .header-right
      margin-left: .15rem
      min-width: 1.04rem
      float: right
      color: #fff
      padding: 0 .1rem
      .icon-jiantouxia
       margin-left: .12rem
</style>