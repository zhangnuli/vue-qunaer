<template>
  <div class="container" @click="handGallary"> 
    <div class="warp">
       <swiper :options="swiperOption">
    <!-- slides -->
    <swiper-slide v-for="(item,index) in imgs" :key="index">
        <img :src="item">
    </swiper-slide>


    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
    </div>
  </div>
    
   
</template>

<script>
export default {
  name: "Gallary",
  props: {
    imgs: {
      type: Array,
      default() {
        return [
          
        ];
      }
    }
  },
  data() {
    return {
      swiperOption: {
        pagination: ".swiper-pagination",
        paginationType: "fraction",
        observeParents:true,
        observer:true
      }
    };
  },

  components: {},

  computed: {},

  methods: {
    handGallary(){
      this.$emit('close')
    }
  }
};
</script>
<style lang='less' scoped>
.swiper-container {
  overflow: inherit;
}
.container {
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  z-index: 99;
  display: flex;
  flex-direction: column;
  justify-content: center;
  background: #000;
  .warp {
    width: 100%;
    height: 0;
    padding-bottom: 100%;

    img {
      width: 100%;
    }
  }
  .swiper-pagination {
    color: #ffffff;
    bottom: -1rem;
  }
}
</style>