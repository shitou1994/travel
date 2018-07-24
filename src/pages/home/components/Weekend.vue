<template>
	<div>
		<div class="recommend-title">周末去哪儿玩</div>
		<ul>
			<li class="item" v-for="item of list" :key="item.id">
				<div class="item-img-wrapper">
					<img class="item-img" :src="item.imgUrl"/>
				</div>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
				</div>
			</li>
		</ul>
	</div>
</template>
<script>
export default {
	name: 'HomeWeekend',
	props:{
		list:Array
	}
	// data () {
	// 	return{
	// 	recommendList: [{
	// 		id: '0001',
	// 		imgUrl: 'http://img1.qunarzz.com/sight/source/1507/d9/2ddc7652fdba16.jpg_r_640x214_5e62f1a3.jpg',
	// 		title: '世界之窗',
	// 		desc: '在玛雅文明的水上乐园中狂欢，激情夏日'
	// 	},{
	// 		id: '0002',
	// 		imgUrl: 'http://img1.qunarzz.com/sight/source/1507/d9/2ddc7652fdba16.jpg_r_640x214_5e62f1a3.jpg',
	// 		title: '世界之窗2',
	// 		desc: '在玛雅文明的水上乐园中狂欢，激情夏日2'
	// 	},{
	// 		id: '0003',
	// 		imgUrl: 'http://img1.qunarzz.com/sight/source/1507/d9/2ddc7652fdba16.jpg_r_640x214_5e62f1a3.jpg',
	// 		title: '世界之窗3',
	// 		desc: '在玛雅文明的水上乐园中狂欢，激情夏日2'
	// 	}]
	// 	}
	// }
}
</script>
<style lang="stylus" scoped>
	@import '../../../assets/styles/mixins.styl'
	.recommend-title
		line-height:2.4rem
		background:#eee
		text-indent:1rem
	.item-img-wrapper
		overflow:hidden
		height:0
		padding-bottom:37%
	.item-img
		width:100%
	.item-info
		padding:0.5rem
		.item-title
			line-height:2.7rem
			font-size:1.6rem
			ellipsis()
		.item-desc
			line-height:2rem
			color:#333
			ellipsis()
</style>