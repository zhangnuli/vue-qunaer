<template>
<div>
    <div class="title">周末去哪儿</div>
    <ul>
        <li class="item border-bottom" v-for="(item,index) of list">
          <div class="warp">
            <img class="item-img" :src="item.imgUrl" alt="">
          </div>
            <div class="item-info">
                <p class="item-title">{{item.title}}</p>
                <p class="item-desc">{{item.desc}}</p>
            </div>
            
        </li>
    </ul>
</div>
</template>
<script>
export default {
  name: "HomeWeekend",
  props:{
    list:Array
  },
  data() {
    return {

    };
  },
  methods: {},
  computed: {},
  components: {}
};
</script>
<style scoped lang="less">
@import "~styles/mixins.less";
.title {
  line-height: 0.8rem;
  background: #eee;
  text-indent: 0.2rem;
}
.item {
  .warp {
    height: 0;
    overflow: hidden;
    padding-bottom: 37.1%;
  }
  .item-img {
    width: 100%;
  }
  .item-info {
    padding: 0.1rem;

    .item-title {
      line-height: 0.54rem;
      font-size: 0.32rem;
      .ellipsis;
    }
    .item-desc {
      line-height: 0.4rem;
       color: #616161;
      .ellipsis;
      font-size: .2rem;
    }
  }
}
</style>