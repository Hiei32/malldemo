<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template #center>首页</template>
    </nav-bar>
    <div>首页</div>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import { getHomeMultidata } from "network/home";

export default {
  name: "Home",
  components: {
    NavBar,
  },
  created() {
    // 1.请求多个数据
    getHomeMultidata().then((res) => {
      console.log(res);
    });
  },
};
</script>

<style lang="scss" scoped>
.home-nav {
  background: deeppink;
}
</style>