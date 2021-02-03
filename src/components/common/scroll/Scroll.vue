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
  props: {
    probeType: {
      type: Number,
      default: 0,
    },
    pullUpLoad: {
      type: Boolean,
      default: false,
    },
  },
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
      click: true,
      probeType: this.probeType,
      pullUpLoad: this.pullUpLoad,
    });
    //滚动监听
    this.scroll.on("scroll", (position) => {
      this.$emit("scrollPosition", position);
    });
    //上拉更多监听
    this.scroll.on("pullingUp", () => {
      this.$emit("scrollUpload");
    });
  },
  methods: {
    backTop(x, y, time = 200) {
      this.scroll.scrollTo(x, y, time);
    },
    finishPullUp() {
      this.scroll.finishPullUp();
    },
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  overflow: hidden;

  .content {
    height: auto;
  }
}
</style>