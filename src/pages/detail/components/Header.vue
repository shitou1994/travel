<template>
  <div>
	  <router-link tag="div" class="header-abs" to="/" v-show="showAbs">
      <div class="iconfont header-abs-back">&#xe600;</div> 
    </router-link>
    <div class="header-fixed" v-show="! showAbs" :style="opacityStyle">
      <router-link to='/'>
        <div class="iconfont header-fixed-back">&#xe600;</div>
      </router-link>
      景点详情
    </div>
  </div>
</template>
<script>
export default {
  name:'DetailHeader',
  data () {
    return {
      showAbs:true,
      opacityStyle:{
        opacity:0
      }
    }
  },
  methods: {
    handleScroll(){
      //console.log(document.documentElement.scrollTop)
      //console.log('scroll')
      const top=document.documentElement.scrollTop
      if(top>60){
        let opacity=top/140
        opacity=opacity>1 ? 1 :opacity
        this.opacityStyle={
          opacity:opacity
        }
        this.showAbs=false
      }else{
        this.showAbs=true
      }
    }
  },
  activated () {
    window.addEventListener('scroll',this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll',this.handleScroll)
  }
}
</script>
<style lang="stylus" scoped>
  @import '../../../assets/styles/varibles.styl'
  .header-abs
    position:absolute
    left:1rem
    top:1rem
    width:4rem
    height:4rem
    text-align:center
    line-height:4rem
    border-radius:2rem
    background:#333
    .header-abs-back
     color:#fff
     font-size:2rem
  .header-fixed
    height:$headerHeight
    line-height:$headerHeight
    overflow:hidden
    text-align:center
    color:#fff
    background:$bgColor
    font-size:1.6rem
    position:fixed
    left:0
    top:0
    right:0
    z-index:2
    .header-fixed-back
      position:absolute
      top:0
      left:0
      width:3.2rem
      text-align:center
      font-size:2rem
      color:#fff
</style>