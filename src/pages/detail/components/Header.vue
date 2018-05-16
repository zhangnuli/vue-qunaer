<template>
  <div>
      <router-link
       tag="div" 
       to="/" 
       class="header-abs" 
       v-show="showAbs"
       ><i class="iconfont icon-fanhui"></i></router-link>
      <div 
        class="header-fixed" 
        v-show="!showAbs"
        :style="opacityStyle"
        >
          景点详情
          <router-link to="/">
      <div class="back iconfont icon-fanhui"></div>
    </router-link>
      </div>
  </div>
</template>

<script>
export default {
  name: "detailHeader",
  data() {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    };
  },
  activated() {
    window.addEventListener("scroll", this.handScroll);
  },
  deactivated() {
    window.removeEventListener("scroll", this.handScroll);
  },
  methods: {
    handScroll() {
      let top = document.documentElement.scrollTop;
      if (top > 60) {
        let opacity = top / 140;
        opacity = opacity > 1 ? 1 : opacity;
        this.opacityStyle = {
          opacity
        };
        this.showAbs = false;
      } else {
        this.showAbs = true;
      }
    }
  },
  components: {},

  computed: {}
};
</script>
<style lang='less' scoped>
@import "~styles/varibles.less";
.header-abs {
  position: absolute;
  left: 0.2rem;
  top: 0.2rem;
  width: 0.8rem;
  height: 0.8rem;
  border-radius: 0.4rem;
  background: rgba(0, 0, 0, 0.8);
  text-align: center;
  line-height: 0.8rem;
  i {
    color: #fff;
    font-size: 0.4rem;
  }
}
.header-fixed {
  z-index:2;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  overflow: hidden;
  height: @headerHeight;
  line-height: 0.86rem;
  text-align: center;
  color: #ffffff;
  background: @bgColor;
  font-size: 0.32rem;
  .back {
    width: 0.64rem;
    text-align: center;
    font-size: 0.4rem;
    position: absolute;
    top: 0;
    left: 0;
    color: #ffffff;
  }
}
</style>