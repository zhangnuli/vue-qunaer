<template>
  <div class="header">
    <div class="header-left"><i class="iconfont icon-fanhui"></i></div>
    <div class="header-input"><i class="iconfont icon-sousuo"></i>请输入城市/景点/游玩主题</div>
    <router-link to="/city">
      <div class="header-right">{{this.$store.state.city}}<i class="iconfont icon-caret"></i></div>
    </router-link>
  </div>
</template>
<script>
  export default {
    name: "HomeHeader",
    props: {
      city: String
    },
    data() {
      return {};
    },
    methods: {},
    computed: {},
    components: {}
  };
</script>
<style scoped lang="less">
  @import "~styles/varibles.less";

  .header {
    display: flex;
    line-height: @headerHeight;
    background: @bgColor;
    color: #fff;
    .header-left {
      width: 0.64rem;
      float: left;
      i {
        display: block;
        font-size: 0.4rem;
        text-align: center;
      }
    }
    .header-input {
      height: 0.64rem;
      flex: 1;
      background: #fff;
      border-radius: 5px;
      margin-top: 0.12rem;
      margin-left: 0.2rem;
      color: #ccc;
      line-height: 0.64rem;
      padding-left: 0.2rem;
    }
    .header-right {
      min-width: 1.04rem;
      padding:0 .1rem;
      float: right;
      text-align: center;
      color: #ffffff;
      i {
        font-size: 0.3rem;
      }
    }
  }
</style>
