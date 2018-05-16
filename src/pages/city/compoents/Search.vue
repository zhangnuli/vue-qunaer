<template>
<div>
    <div class="search">
      <input v-model="keyword" type="text" class="search-input" placeholder="输入城市名或者拼音">
    </div>
    <div class="search-content" ref="search" v-show="keyword">
        <ul>
            <li class="border-bottom" v-for="item of list" :key="item.id" @click="handCityClick(item.name)">{{item.name}}</li>
            <li class="border-bottom" v-show="hasNoData">没有找到相关城市</li>
        </ul>
    </div>
</div>
</template>

<script>
import Bscroll from "better-scroll"
export default {
  name: "CitySearch",
  props:{
      cities:Object
  },
  data(){
      return{
          keyword:'',
          list:[],
          timer:null
      }
  },
  watch:{
      keyword(){
          if (this.timer) {
              clearTimeout(this.timer)
          }
          if(!this.keyword){
              this.list=[];
              return;
          }
          this.timer = setTimeout(()=>{
              const res = [];
              for(let i in this.cities){
                  this.cities[i].forEach((value) => {
                    if (value.spell.indexOf(this.keyword)>-1||value.name.indexOf(this.keyword)>-1) {
                        res.push(value)
                    }  
                  });
              }
              this.list=res;
          },100)
      }
  },
  methods:{
       handCityClick(city){
      this.$store.commit('changeCity',city);
      this.$router.push('/')
      
    }
  },
  computed:{
      hasNoData(){
          return !this.list.length
      }
  },
  mounted(){
      this.scoll = new Bscroll(this.$refs.search)
  }
};
</script>

<style scoped lang="less">
@import "~styles/varibles.less";
.search {
  height: 0.72rem;
  padding: 0 0.1rem;
  background: @bgColor;
  .search-input {
    box-sizing: border-box;
    padding: 0 0.1rem;
    height: 0.62rem;
    line-height: 0.62rem;
    width: 100%;
    text-align: center;
    border-radius: 0.06rem;
    color: #666;
  }
}
.search-content {
  position: absolute;
  top: 1.58rem;
  left: 0;
  right: 0;
  bottom: 0;
  overflow: hidden;
  z-index: 1;
  background: #eeeeee;
  li{
      line-height: 0.62rem;
      padding: 0.2rem;
      background: #ffffff;
      color: #666666
  }
}
</style>
