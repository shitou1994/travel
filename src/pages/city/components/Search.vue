<template>
  <div>
    <div class="search">
      <input v-model="keyword" class="search-input" type="text" placeholder="输入城市名和拼音"/>
    </div>
    <div class="search-content" ref="search" v-show="keyword">
      <ul>
        <li class="search-item" v-for="item of list" @click="handleCityClick(item.name)">{{item.name}}</li>
        <li class="search-item" v-show="hasNoData">没有找到匹配数据</li>
      </ul>
    </div>
  </div>	
</template>
<script>
  import BScroll from 'better-scroll'
  import { mapState, mapMutations} from 'vuex'
  export default {
    name:'CitySearch',
    props: {
      cities:Object
    },
    data () {
      return {
        keyword:'',
        list:[],
        timer:null
      }
    },
    computed:{
      hasNoData () {
        return !this.list.length
      }
    },
    watch:{
      keyword (){
        if(this.timer){
          clearTimeout(this.timer)
        }
        if(!this.keyword){
          this.list=[]
          return
        }
        this.timer=setTimeout(() =>{
          const result =[]
          for (let i in this.cities){
            this.cities[i].forEach((value)=>{
              if(value.spell.indexOf(this.keyword)>-1||
                value.name.indexOf(this.keyword)>-1){
                  result.push(value)
              }
            })
          }
          this.list=result
        },100)
      }
    },
    methods: {
     handleCityClick(city){
      //this.$store.dispatch('changeCity',city)
      this.changeCity(city)
      this.$router.push('/')
     },
     ...mapMutations(['changeCity'])
    },
    mounted () {
      this.scroll=new BScroll(this.$refs.search)
    }
  }
</script>
<style lang="stylus" scoped>
  @import '../../../assets/styles/varibles.styl'
  .search
    height:3.6rem
    padding:0 0.5rem
    background:$bgColor
    .search-input
      box-sizing:border-box
      width:100%
      height:3.1rem
      line-height:3.1rem
      text-align:center
      border-radius:0.4rem
      color:#666
      padding:0 0.8rem
      margin-bottm:0.5rem
  .search-content
    z-index:1
    overflow:hidden
    position:absolute
    top:7.9rem
    left:0
    right:0
    bottom:0
    background:#eee
    .search-item
      line-height:3.1rem
      padding-left:1rem
      background:#fff
      border-bottom:0.1rem solid #eee
      color:#666
</style>