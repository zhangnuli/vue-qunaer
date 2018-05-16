<!--  -->
<template>
<div>
  <div class="banner" @click="handBanner">
      <img :src="bannerImg"
      class="banner-img"
      >
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-num">
          <i class="iconfont icon-tupian"></i>
          {{bannerNum}}
        </div>
      </div>
     </div>  
     <fade>
        <gallary :imgs="gallaryImg" v-show="showGallary" @close="handClose"></gallary>
     </fade>

  </div>
</template>

<script>
import Gallary from "../../common/gallary/Gallary";
import Fade from "../../fade/Fade";
export default {
  name: "DetailBanner",
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImg: Array
  },
  data() {
    return {
      showGallary: false
    };
  },

  components: {
    Gallary,
    Fade
  },

  computed: {
    bannerNum() {
      return this.gallaryImg.length;
    }
  },

  methods: {
    handBanner() {
      this.showGallary = true;
    },
    handClose() {
      this.showGallary = false;
    }
  }
};
</script>
<style lang='less' scoped>
.banner {
  position: relative;
  overflow: hideen;
  height: 0;
  padding-bottom: 55%;
  .banner-img {
    width: 100%;
  }
  .banner-info {
    display: flex;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    line-height: 0.6rem;
    color: #fff;
    background-image: linear-gradient(
      top,
      rgba(0, 0, 0, 0),
      rgba(0, 0, 0, 0.8)
    );
    .banner-title {
      flex: 1;
      font-size: 0.32rem;
      padding: 0 0.2rem;
    }
    .banner-num {
      margin-top: 0.14rem;
      padding: 0 0.4rem;
      height: 0.4rem;
      line-height: 0.4rem;
      border-radius: 0.2rem;
      font-size: 0.24rem;
      background: rgba(0, 0, 0, 0.8);
      text-align: center;
      i {
        font-size: 0.24rem;
        margin-right: 0.1rem;
      }
    }
  }
}
</style>