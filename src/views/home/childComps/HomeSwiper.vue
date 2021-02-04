<template>
  <swiper>
    <swiper-item v-for="(item, index) in banners" :key="index">
      <a href="item.link">
        <img :src="item.image" alt="" @load="imageLoad" />
      </a>
    </swiper-item>
  </swiper>
</template>

<script>
import { Swiper, SwiperItem } from "components/common/swiper"; //swiper下的index.js导出2个对象
export default {
  name: "HomeSwiper",
  props: {
    banners: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data() {
    return {
      isLoad: false,
    };
  },
  components: {
    Swiper,
    SwiperItem,
  },
  methods: {
    imageLoad() {
      if (!this.isLoad) {
        this.$emit("swiperImageLoaded");
        this.isLoad = true;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
</style>