<!--  -->
<template>
  <div>
      <detail-banner 
      :sightName="sightName" 
      :bannerImg="bannerImg" :gallaryImg="gallaryImg"></detail-banner>
      <detail-header></detail-header>
      <div class="cap">
        <detail-list :list="list"></detail-list>
      </div>
  </div>
</template>

<script>
import DetailBanner from "./components/Banner";
import DetailHeader from "./components/Header";
import DetailList from "./components/List";
import axios from "axios";
export default {
  name: "Detail",
  data() {
    return {
      sightName: "",
      bannerImg: "",
      gallaryImg: [],
      list: []
    };
  },

  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  mounted() {
    this.getDetailInfo();
  },
  computed: {},

  methods: {
    getDetailInfo() {
      axios
        .get("api/detail.json", {
          params: { id: this.$route.params.id }
        })
        .then(this.handGetInfoSucc);
    },
    handGetInfoSucc(res) {
      res = res.data;
      if (res.ret && res.data) {
        let data = res.data;
        this.sightName = data.sightName;
        this.bannerImg = data.bannerImg;
        this.gallaryImg = data.gallaryImgs;
        this.list = data.list;
        console.log(data.list);
        
      }
    }
  }
};
</script>
<style lang='less' scoped>
.cap {
  height: 50rem;
}
</style>