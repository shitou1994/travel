<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <div class="title boeder-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button-wrapper">
            <div class="button">{{this.currentCity}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title boeder-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button-wrapper" v-for="item of hot" :key="item.id" @click="handleCityClick(item.name)">
            <div class="button">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) of cities"  :key="key" :ref="key"  >
        <div class="title boeder-topbottom">{{key}}</div>
        <ul class="item-list">
          <li class="item" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</li>
        </ul>
      </div>
    </div>
  </div>	
</template>
<script>
import BScroll from 'better-scroll'
import { mapState, mapMutations} from 'vuex'
export default {
  name:'CityList',
  props:{
    hot:Array,
    cities:Object,
    letter:String
  },
  computed:{
    ...mapState({
      currentCity:'city'
    })
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
    this.scroll=new BScroll(this.$refs.wrapper)
  },
  //监听器
  watch:{
    letter(){
      //console.log(this.letter)
      if(this.letter){
        const element=this.$refs[this.letter][0]
        console.log(element)
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import '../../../assets/styles/varibles.styl'
  .boeder-topbottom
    &:bofore
      border-color:#ccc
    &:after
      border-color:#ccc
  .list
    position:absolute
    top:7.9rem
    left:0
    right:0
    bottom:0
    overflow:hidden
    .title
      line-height:2.2rem
      background:#eee
      padding-left:1rem
      font-size:1.3rem
    .button-list
      overflow:hidden
      padding:0.5rem 0.3rem 0.5rem 0.5rem
      .button-wrapper
        width:33.33%
        float:left
        .button
          text-align:center
          margin:0.5rem
          padding:0.5rem 0
          border:0.1rem solid #ccc
    .item-list
      .item
        line-height:2.8rem
        padding-left:1rem
        color:#666
        border-bottom:0.1rem solid #ccc  
</style>