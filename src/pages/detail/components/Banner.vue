<template>
  <div>
	<div class="banner" @click="handleBannerClick">
		<img class="banner-img" src="//img1.qunarzz.com/sight/p0/1508/2e/d9363ce50a88c8c5ff5a138c67687cd4.water.jpg_600x330_28bda6b0.jpg">
		<div class="banner-info">
			<div class="banner-title">深圳野生动物园(AAAA景区)</div>
			<div class="banner-number"><span class="iconfont banner-icon">&#xe63a;</span>39</div>
		</div>
	</div>
  <fade-animation>
	   <common-gallary :imgs="imgs" v-show="showGallary" @close="handleGallaryClose"></common-gallary>
  </fade-animation>
  </div>
</template>
<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
  name:'DetailBanner',
  props:{
    
  },
  data () {
  	return {
  	  showGallary:false,
  	  imgs:['//img1.qunarzz.com/sight/p0/1508/2e/d9363ce50a88c8c5ff5a138c67687cd4.water.jpg_600x330_28bda6b0.jpg','//img1.qunarzz.com/sight/p0/1805/17/176c2114bb8ae255a3.water.png_600x330_3cf0f62e.png']
  	}
  },
  methods:{
  	handleBannerClick(){
  		this.showGallary=true
  	},
  	handleGallaryClose(){
  		this.showGallary=false
  	}
  },
  components:{
  	CommonGallary,
    FadeAnimation
  }
}
</script>
<style lang="stylus" scoped>
  .banner
    position:relative
    overflow:hidden
    height:0
    padding-bottom:55%
    .banner-img
      width:100%
    .banner-info
      dispaly:flex
      flex-direction:row-reverse
      position:absolute
      left:0
      right:0
      bottom:0
      line-height:3rem
      color:#fff
      background-image:linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
      .banner-title
        flex:1
        font-size:1.6rem
        float:left
      .banner-number
        padding:0 2rem
        border-radius:1rem
        font-size:1.6rem
        float:right
        .banner-icon
          margin-right:0.6rem
</style>