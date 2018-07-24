<template>
  <div>
	  <div class="item" v-for="(item,index) of list" :key="index">
      <div class="item-title">
        <span class="item-title-icon"></span>
        {{item.title}}
      </div>
      <div v-if="item.children" class="item-chilren">
        <detail-list :list="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name:'DetailList',
  props:{
    list:Array
  }
}
</script>
<style lang="stylus" scoped>
  .item-title
    line-height:4rem
    font-size:1.6rem
    padding:0 1rem
    border-bottom:1px solid #ebebeb
    .item-title-icon
      width:1.8rem
      height:1.8rem
      display:inline-block
      margin-right:0.5rem

      background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -7rem no-repeat;
      background-size: 2.4rem 2.4rem
  .item-chilren
    padding:0 1rem
</style>