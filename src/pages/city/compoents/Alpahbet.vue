<!--  -->
<template>
  <ul class="list">
      <li class="item" 
      v-for="item of letters" 
      :key="item" 
      @click="hand" 
      @touchstart.prevent="handTouchStart" @touchmove="handTouchMove" @touchend="handTouchEnd" 
      :ref="item"
      >
      {{item}}
      </li>
  </ul>
</template>

<script>
export default {
  name: "CityAlpahbet",
  computed: {
    letters() {
      let letters = [];
      for (let i in this.cities) {
        letters.push(i);
      }
      return letters;
    }
  },
  data() {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    };
  },
  updated() {
    this.startY = this.$refs["A"][0].offsetTop;
  },
  props: {
    cities: Object
  },
  methods: {
    hand(e) {
      this.$emit("change", e.target.innerText);
    },
    handTouchStart() {
      this.touchStatus = true;
    },
    handTouchMove(e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer);
        }
        this.timer = setTimeout(() => {
          let touchY = e.touches[0].clientY - 79;
          let index = Math.floor((touchY - this.startY) / 22);
          if (index >= 0 && index < this.letters.length) {
            this.$emit("change", this.letters[index]);
          }
        }, 16);
      }
    },
    handTouchEnd() {
      this.touchStatus = false;
    }
  }
};
</script>
<style lang='less' scoped>
@import "~styles/varibles.less";
.list {
  position: absolute;
  top: 1.58rem;
  right: 0;
  bottom: 0;
  width: 0.4rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  .item {
    text-align: center;
    line-height: 0.44rem;
    color: @bgColor;
  }
}
</style>