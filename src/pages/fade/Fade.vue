
<template>
  <transition>
      <slot></slot>
  </transition>
</template>

<script>
export default {
  name:'Fade',
  data () {
    return {
    };
  },

  components: {},

  computed: {},

  mounted: {},

  methods: {}
}

</script>
<style lang='less' scoped>
.v-enter,.v-leave-to{
    opacity: 0;
}
.v-enter-active,.v-leave-active{
    transition: opacity .5s;
}
</style>