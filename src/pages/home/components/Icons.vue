<template>
  <div class="icons">
	<swiper :options="swiperOption">
		<swiper-slide  v-for="(page,index) of pages" :key="index">
	  	<div class="icon" v-for="item of page" :key="item.id">
	  		<div class="icon-img">
	  			<img class="icon-img-content" :src="item.imgUrl"/>
	  		</div>
	  		<p class="icon-desc">{{item.desc}}</p>
	  	</div>
		</swiper-slide>
		<div class="swiper-pagination"  slot="pagination"></div>
	</swiper>
  </div>
</template>
<script>
export default {
	name: 'HomeIcons',
	props: {
		list:Array
	},
	data (){
		return {
			swiperOption:{
				autoplay:false
			}
		}
	},
	computed:{
		pages () {
			const pages = []
			this.list.forEach((item,index) => {
				const page=Math.floor(index/8)
				if(!pages[page]){
					pages[page]=[]
				}
				pages[page].push(item)
			})
			return pages
		}
	}

}
</script>
<style lang="stylus" scoped>
	@import '../../../assets/styles/varibles.styl'
	@import '../../../assets/styles/mixins.styl'
	.icons >>> .swiper-pagination-bullet-active
		background:blue
	.icons >>> .swiper-container 
		width:100%
		overflow:hidden
		height:0
		padding-bottom:50%
	.icon
		position:relative
		overflow:hidden
		float:left
		width:25%
		height:0
		padding-bottom:25%
		.icon-img
			position:absolute
			left:0
			top:0
			right:0
			bottom:2.2rem
			box-sizing:border-box
			padding:0.5rem
			.icon-img-content
				height:100%
				display:block
				margin:0 auto
		.icon-desc
			position:absolute
			left:0
			right:0
			bottom:0
			height:2.2rem
			line-height:2.2rem
			color:$darkTextColor
			text-align:center
			ellipsis()
</style>