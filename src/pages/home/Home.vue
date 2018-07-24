<template>
  <div>
	  <home-header></home-header>
	  <home-swiper :list="swiperList"></home-swiper>
	  <home-icons :list="iconList"></home-icons>
	  <home-recommend :list="recommendList"></home-recommend>
	  <home-weekend :list="weekendList"></home-weekend>
  </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import {mapState} from 'vuex'
export default {
	name : 'Home',
	components : {
		HomeHeader: HomeHeader,
		HomeSwiper: HomeSwiper,
		HomeIcons:  HomeIcons,
		HomeRecommend: HomeRecommend,
		HomeWeekend: HomeWeekend
	},
	data () {
		return {
			lastCity:'',
			swiperList:[],
			iconList:[],
			recommendList:[],
			weekendList:[]
		}
	},
	computed:{
	  ...mapState(['city'])
	},
	methods : {
		getHomeInfo(){
			axios.get('/api/index.json?city=' +this.city).then(this.getHomeInfoSucc)
		},
		getHomeInfoSucc (res) {	
			//var data = res.data;
		var data = eval('('+res.data+')')
		this.swiperList=data.data.swiperList
		this.iconList=data.data.iconList
		this.recommendList=data.data.recommendList
		this.weekendList=data.data.weekendList
			//
			//console.log(data)
			//res=res.data
			//const data=res.ret
			//console.log(data)
			// if(res.ret && res.data){
			// 	const data=res.data
			// 	this.city=data.city
			// 	// const data=res.data
			// 	// alert(res)
			// 	// this.city=data.city
			// 	// this.swiperList=data.swiperList
			// }
		}
	},
	mounted () {
		this.lastCity=this.city
		this.getHomeInfo()
	},
	activated () {
		if(this.lastCity !== this.city){
			this.lastCity=this.city
			this.getHomeInfo()
		}
		//console.log('activated')
	}
}
</script>
<style>
	
</style>