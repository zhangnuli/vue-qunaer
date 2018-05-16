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
import HomeHeader from "./compoents/Header";
import HomeSwiper from "./compoents/Swiper";
import HomeIcons from "./compoents/icons";
import HomeRecommend from "./compoents/Recommend";
import HomeWeekend from "./compoents/Weekend";
import axios from "axios";
import { mapState } from "vuex";
export default {
  data() {
    return {
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: [],
      lastCity: ""
    };
  },
  mounted() {
    this.lastCity = this.city;
    this.getHomeInfo();
  },
  methods: {
    getHomeInfo() {
      axios.get("/api/index.json?city=" + this.city).then(this.getHomeInfoSucc);
    },
    getHomeInfoSucc(res) {
      res = res.data;
      if (res.ret && res.data) {
        let data = res.data;
        this.swiperList = data.swiperList;
        this.iconList = data.iconList;
        this.recommendList = data.recommendList;
        this.weekendList = data.weekendList;
      }
    }
  },
  activated() {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city;
      this.getHomeInfo();
    }
  },
  computed: {
    ...mapState(["city"])
  },
  components: { HomeHeader, HomeSwiper, HomeIcons, HomeRecommend, HomeWeekend }
};
</script>
<style scoped>
</style>