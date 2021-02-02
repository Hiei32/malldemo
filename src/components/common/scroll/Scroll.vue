<template>
  <div class="wrapper" ref="wraperObj">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from "better-scroll";
export default {
  name: "Scroll",
  data() {
    return {
      scroll: null,
    };
  },
  components: {
    BScroll,
  },
  mounted() {
    //通过ref来取得组件对象
    this.scroll = new BScroll(this.$refs.wraperObj, {
      probeType: 3,
      click: true,
      pullUpLoad: true,
    });
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  overflow: hidden;

  .content{
    height: auto;
  }
}
</style>