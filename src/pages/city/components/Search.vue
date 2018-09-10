<template>
  <div>
    <div class="search">
    <input type="text" v-model="keyword"
    class="search-input" placeholder="输入城市名或者拼音">
    </div>
    <div class="search-content" 
       v-show="keyword" ref="search">
      <ul>
        <li class="search-item border-bottom"
        v-for="(item,index) in list" 
        :key="index"
        @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item border-bottom"
          v-show="!this.list.length" >没有找到匹配项</li> 
      </ul>
    </div>
  </div>
</template>

<script>
  import Bscroll from 'better-scroll'
  export default {
    name: 'CitySearch',
    props: {
      cities: Object
    },
    data(){
      return {
        keyword: '',
        list: [],
        timer: null
      }
    },
    watch: {
      keyword(){
        if(this.timer){
          clearTimeout(this.timer)
        }
        if( !this.keyword ){
          return this.list = '' 
        }
        this.timer = setTimeout( ()=>{
          const result = []
          for( let i in this.cities ){
            this.cities[i].forEach( (value)=>{
              if(value.spell.indexOf(this.keyword)>-1 ||value.name.indexOf(this.keyword)>-1){
                result.push(value)
              }
            })
          }
          this.list = result
        },100 )
      }
    },
    methods: {
       handleCityClick(city){
        this.$store.dispatch( 'changeCity', city )
        this.$router.push('/')
      }
    },
    mounted(){
      this.scroll = new Bscroll(this.$refs.search)
    }
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
    .search-content
      z-index: 1
      overflow: hidden
      position: absolute
      top: 1.58rem
      left: 0
      right: 0
      bottom: 0
      background: #eee
      .search-item
        line-height:  .62rem
        padding: .2rem
        color: #666
        background: #fff
</style>