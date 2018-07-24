<template>
	<div>
		<div class="recommend-title">热销推荐</div>
		<ul>
			<router-link tag="li" class="item" v-for="item of list" :key="item.id" :to="'/detail/' + item.id">
				<img class="item-img" :src="item.imgUrl"/>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<button class="item-button"> 查看详情</button>
				</div>
			</router-link>
			
		</ul>
	</div>
</template>
<script>
export default {
	name: 'HomeRecommend',
	props:{
		list:Array
	}
}
</script>
<style lang="stylus" scoped>
	@import '../../../assets/styles/mixins.styl'
	.recommend-title
		line-height:2.4rem
		background:#eee
		text-indent:1rem
	.item
		display:flex
		line-height:9.5rem
		.item-img
			width:8.5rem
			height:8.5rem
			padding:0.5rem
		.item-info
			flex:1
			padding:0.5rem
			min-width:0
			.item-title
				line-height:2.7rem
				font-size:1.6rem
				ellipsis()
			.item-desc
				line-height:2rem
				color:#333
				ellipsis()
			.item-button
				background:#ff9300
				padding:0.3rem 1rem
				border-radius:0.3rem
				margin-top:1rem
				color:#fff
				display: inherit
				border:none
</style>