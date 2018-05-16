<template>
<div class="warp">
    <swiper :options="swiperOption" v-if="showSwiper">
    <!-- slides -->
    <swiper-slide v-for="(item,index) of list" :key="index">
        <img :src="item.imgUrl" class="swiper-img">
    </swiper-slide>

    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</div>
  
</template>
<script>
export default {
  name: "HomeSwiper",
  props: {
    list: Array
  },
  data() {
    return {
      swiperOption: {
        pagination: ".swiper-pagination",
        loop: true,
        autoplay: 2000
      }
    };
  },
  methods: {},
  computed: {
    showSwiper(){
      return this.list.length
    }
  },
  components: {}
};
</script>
<style scoped lang="less">
.warp {
  width: 100%;
  height: 0;
  overflow: hidden;
  padding-bottom: 31.25%;
  .swiper-img {
    width: 100%;
  }
}
</style>