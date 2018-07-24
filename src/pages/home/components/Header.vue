<template>
	<div class="header">
		<div class="header-left">
			<span class="iconfont back-icon">&#xe600;</span>
		</div>
		<div class="header-input"><span class="iconfont in-icon">&#xe60b;</span>输入城市/景点/游玩主题</div>
		<router-link to='/city'>
		  <div class="header-right">{{this.city}}<span class="iconfont arrow-icon">&#xe6aa;</span></div>
		</router-link>
	</div>
</template>
<script>
import { mapState,mapGetters } from 'vuex'
export default {
	name: 'HomeHeader',
	computed:{
	  ...mapState(['city']),
	  ...mapGetters(['doubleCity'])
	}
}
</script>
<style lang="stylus" scoped>
	@import '../../../assets/styles/varibles.styl'
	.header
		display:flex
		height:$headerHeight
		line-height:$headerHeight
		background:$bgColor
		color:#fff
		.header-left
			width:3.2rem
			float:left
			text-align:center
			.back-icon
				font-size:2rem
		.header-input
			flex:1
			margin-top:0.6rem
			height:3.1rem
			line-height:3.1rem
			background:#fff
			border-radius:0.4rem
			color:#ccc
			padding-left:2rem
			.in-icon
				font-size:1.6rem
		.header-right
			min-width:6.2rem
			padding:0 0.5rem
			float:right
			text-align:center
			color:#fff
			.arrow-icon
				font-size:1.6rem
</style>