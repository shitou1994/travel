<template>
  <div class="wrapper">
  <swiper :options="swiperOption" v-if="showSwiper">
    <!-- slides -->
    <swiper-slide v-for="item of list" :key="item.id">
    	<img class="swiper-img" :src="item.imgUrl">
    </swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
  </div>
</template>
<script>
export default {
	name: 'HomeSwiper',
	props:{
		list:Array
	},
	data() {
		return {
			swiperOption:{
				pagination: '.swiper-pagination',
				loop:true
			},
			// swiperList: [{
			// 	id:'0001',
			// 	imgUrl:'http://img1.qunarzz.com/piao/fusion/1805/77/f63bd04dd5319602.jpg_750x200_6ba8e0ca.jpg'
			// },{
			// 	id:'0002',
			// 	imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/f2/91b285a08ee21c02.jpg_750x200_8a73fd08.jpg'
			// }]
		}
	},
	computed:{
		showSwiper ()  {
			return this.list.length
		}
	}

}
</script>
<style lang="stylus" scoped>
	.wrapper >>> .swiper-pagination-bullet-active
		background:#fff
	.wrapper
		overflow:hidden
		width:100%
		height:0
		padding-bottom:26.67%
		background:#eee
		.swiper-img
			width:100%
</style>