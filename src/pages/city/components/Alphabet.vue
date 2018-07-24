<template>
  <ul class="list">
    <li class="item" v-for="item of letters" :key="item" @click="handleLetterClick"@touchstart.prevent="handleTouchStart" @touchmove="handleTouchMove" @touchend="handleTouchEnd" :ref="item">{{item}}</li>
  </ul>	
</template>
<script>
  export default {
    name:'CityAlphabet',
    props:{
      cities:Object
    },
    computed:{
      letters() {
        const letters=[]
        for(let i in this.cities){
          letters.push(i)
        }
        return letters
        // ['A','B']
      }
    },
    data (){
      return{
        touchStatus:false,
        startY:0,
        timer:null
      }
    },
    updated (){
      this.startY=this.$refs['A'][0].offsetTop
    },
    methods:{
      handleLetterClick(e){
        this.$emit('change',e.target.innerText)
        //console.log(e.target.innerText)
      },
      handleTouchStart(){
        this.touchStatus=true
      },
      handleTouchMove(e){
        if(this.touchStatus){
          if(this.timer){
            clearTimeout(this.timer)
          }
          this.timer=setTimeout(()=>{
            //const startY=this.$refs['A'][0].offsetTop
          const touchY=e.touches[0].clientY-79
          const index=Math.floor((touchY-this.startY)/22)
          if(index>=0 && index <this.letters.length){
            this.$emit('change',this.letters[index])
          }    
          },16)       
        }
      },
      handleTouchEnd(){
        this.touchStatus=false
      }
    }
  }
</script>
<style lang="stylus" scoped>
  @import '../../../assets/styles/varibles.styl'
  .list
    display:flex
    flex-direction:column
    justify-content:center
    position:absolute
    top:7.9rem
    right:0
    bottom:0
    width:2rem
    .item
      line-height:2.2rem
      text-align:center
      color:$bgColor
</style>