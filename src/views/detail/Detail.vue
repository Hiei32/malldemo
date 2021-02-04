<template>
  <div class="detail">
    <detail-nav-bar />
    <h2>{{ iid }}</h2>
  </div>
</template>

<script>
import DetailNavBar from "./childComps/DetailNavBar.vue";
export default {
  name: "Detail",
  data() {
    return {
      iid: null,
    };
  },
  components: {
    DetailNavBar,
  },
  created() {
    this.iid = this.$route.params.iid;
  },
};
</script>

<style lang="scss" scoped>
.detail {
  width: 100%;
  height: 100vh;
  background: #fff;
  position: relative;
  z-index: 20;
}
</style>