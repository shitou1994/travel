
<template>
  <div>
  	<detail-banner :sightName="sightName"></detail-banner>
  	<detail-header></detail-header>
  	<div class="content">
      <detail-list :list="list"></detail-list> 
    </div>
  </div>
</template>
<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'
export default {
  name:'Detail',
  components:{
  	DetailBanner:DetailBanner,
  	DetailHeader,
    DetailList
  },
  data () {
    return {
      sightName:'',
      list:[{
        title:'成人票',
        children:[{
          title:'成人三馆联票',
          children:[{
            title:'成人馆联票-某一连锁店'
          }]
        },{
          title:'成人武馆馆联票'
        }]
      },{
        title:'学生票'
      },{
        title:'儿童票'
      },{
        title:'特惠票'
      }]
    }
  },
  methods:{
    getDetailInfo(){
      axios.get('api/detail.json',{
        params:{
          id:this.$route.params.id
        }
      }).then(this.handleGetDataSucc)
    },
    handleGetDataSucc(res){
      // console.log(res)
      // //res=res.data
      // var res=eval('('+res.data+')')
      // //console.log(res)
      // //console.log(res.ret)
      // if(res.ret && res.data){
      //    this.sightName=res.data.sightName
      // }
    }
  }, 
  mounted(){
    this.getDetailInfo()
  }
}
</script>
<style lang="stylus" scoped>
  .content
    height:100rem
</style>