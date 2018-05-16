<template>
<div class="icons">
     <swiper :options="swiperOption">
         <swiper-slide v-for="(page,index) of pages" :key="index">
            <div class="icon" v-for="item of page" :key="item.id">
                <div class="icon-img">
                    <img :src="item.imgUrl" alt="">
                </div>
            <p>{{item.desc}}</p>
            </div>
        </swiper-slide>
     </swiper>
</div>
</template>
<script>
export default {
  name: "HomeIcons",
  props:{
    list:Array
  },
  data() {
    return {
      swiperOption: {},
    };
  },
  methods: {},
  computed: {
    pages() {
      const pages = [];
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8);
        if (!pages[page]) {
          pages[page] = [];
        }
        pages[page].push(item);
      });
      return pages;
    }
  },
  components: {}
};
</script>
<style scoped lang="less">
@import "~styles/varibles.less";
@import "~styles/mixins.less";
.icons {
  height: 0;
  padding-bottom: 50%;
  overflow: hidden;
  margin-top: 0.1rem;
  .icon {
    overflow: hidden;
    width: 25%;
    height: 0;
    float: left;
    padding-bottom: 25%;
    position: relative;
    .icon-img {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0.44rem;
      box-sizing: boeder-box;
      padding: 0.1rem;
      img {
        height: 100%;
        display: block;
        margin: 0 auto;
      }
    }
    p {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      height: 0.44rem;
      line-height: 0.44rem;
      color: @darkTextColor;
      text-align: center;
      .ellipsis;
    }
  }
}
</style>