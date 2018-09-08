<template>
  <div class="search">
    <input type="text" class="search-input"
    placeholder="输入城市名或者拼音">
  </div>
</template>

<script>
  export default {
    name: 'CitySearch'
  }
</script>

<style scoped lang="stylus">
  @import "~@/assets/styles/varibles.styl"
   .search 
      height: .72rem
      padding: 0 .1rem
      background: $bgColor
      .search-input
        height: .62rem
        line-height: .62rem
        width: 100%
        text-align: center
        border-radius: .06rem
        color: #666
        padding: 0 .1rem
        box-sizing: border-box
</style>