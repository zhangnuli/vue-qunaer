<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="back iconfont icon-fanhui"></div>
    </router-link>
    </div>
</template>
<script>
  export default {
    name: 'HomeHeader',
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
    position: relative;
    overflow: hidden;
    height: @headerHeight;
    line-height: .86rem;
    text-align: center;
    color: #ffffff;
    background: @bgColor;
    font-size: .32rem;
    .back{
      width: .64rem;
      text-align: center;
      font-size: .4rem;
      position: absolute;
      top: 0;
      left: 0;
      color: #ffffff;
    }
  }
</style>



