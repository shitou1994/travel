<template>
  <div class="header">
    城市选择
    <router-link to='/'>
    	<div class="iconfont header-back">&#xe600;</div>
    </router-link>
  </div>	
</template>
<script>
  export default {
    name:'CityHeader'
  }
</script>
<style lang="stylus" scoped>
  @import '../../../assets/styles/varibles.styl'
  .header
    height:$headerHeight
    line-height:$headerHeight
    overflow:hidden
    text-align:center
    color:#fff
    background:$bgColor
    font-size:1.6rem
    position:relative
    .header-back
      position:absolute
      top:0
      left:0
      width:3.2rem
      text-align:center
      font-size:2rem
      color:#fff
</style>