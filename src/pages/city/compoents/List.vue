<!--  -->
<template>
  <div class="list" ref="warp">
    <div>
    <div class="area">
      <div class="title border-topbottom">当前城市</div>
      <div class="btn-list">
        <div class="btn-warp">
          <div class="btn">{{this.$store.state.city}}</div>
        </div>
    </div>
    <div class="area  border-topbottom">
      <div class="title  border-topbottom">热门城市</div>
       <div class="btn-list">
          <div class="btn-warp"  v-for="item of hot" :key="item.id" @click="handCityClick(item.name)">
            <div class="btn">{{item.name}}</div>
          </div>
       </div>
    </div>
    <div class="area" v-for=" (item,key) of cities" :ref="key">
      <div class="title">{{key}}</div>
      <div class="item-list">
        <div class="item border-bottom" v-for="innerItem of item" :key="innerItem.id"  @click="handCityClick(innerItem.name)">{{innerItem.name}}</div>
      </div>
    </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from "better-scroll";
export default {
  props: {
    hot: Array,
    cities: Object,
    letter: String
  },
  name: "CityList",
  data() {
    return {};
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.warp,{click:true});
  },
  watch: {
    letter() {
      if (this.letter) {
        let ele = this.$refs[this.letter][0];
          this.scroll.scrollToElement(ele)
      }
    }
  },
  components: {},

  computed: {},

  methods: {
    handCityClick(city){
      this.$store.commit('changeCity',city);
      this.$router.push('/')
      
    }
  }
};
</script>
<style lang='less' scoped>
.border-topbottom {
  &:bofore {
    border-color: #ccc;
  }
  &:after {
    border-color: #ccc;
  }
}
.border-bottom {
  &:bofore {
    border-color: #ccc;
  }
}
.list {
  overflow: hidden;
  position: absolute;
  top: 1.58rem;
  left: 0;
  right: 0;
  bottom: 0;
  .title {
    line-height: 0.54rem;
    background-color: #eeeeee;
    color: #666;
    font-size: 0.26rem;
  }
  .btn-list {
    padding: 0.1rem 0.6rem 0.1rem 0.1rem;
    overflow: hidden;
    .btn-warp {
      float: left;
      width: 33.33%;
      .btn {
        margin: 0.1rem;
        text-align: center;
        border: 0.02rem solid #ccc;
        padding: 0.1rem 0;
        border-radius: 0.6rem;
      }
    }
  }
  .item-list {
    .item {
      line-height: 0.76rem;
      padding-left: 0.2rem;
    }
  }
}
</style>
