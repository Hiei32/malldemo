<template>
  <tab-bar>
    <tab-bar-item path="/home">
      <template #icon>
        <img src="~assets/img/tabbar/tab01.svg" alt="" class="default-img" />
        <img src="~assets/img/tabbar/tab01-act.svg" alt="" class="active-img" />
      </template>
      <template #text>
        <span>首页</span>
      </template>
    </tab-bar-item>
    <tab-bar-item path="/category">
      <template #icon>
        <img src="~assets/img/tabbar/tab02.svg" alt="" class="default-img" />
        <img src="~assets/img/tabbar/tab02-act.svg" alt="" class="active-img" />
      </template>
      <template #text>
        <span>分类</span>
      </template>
    </tab-bar-item>
    <tab-bar-item path="/cart">
      <template #icon>
        <img src="~assets/img/tabbar/tab03.svg" alt="" class="default-img" />
        <img src="~assets/img/tabbar/tab03-act.svg" alt="" class="active-img" />
      </template>
      <template #text>
        <span>购物车</span>
      </template>
    </tab-bar-item>
    <tab-bar-item path="/profile">
      <template #icon>
        <img src="~assets/img/tabbar/tab04.svg" alt="" class="default-img" />
        <img src="~assets/img/tabbar/tab04-act.svg" alt="" class="active-img" />
      </template>
      <template #text>
        <span>我的</span>
      </template>
    </tab-bar-item>
  </tab-bar>
</template>

<script>
import TabBar from "components/common/tabbar/TabBar";
import TabBarItem from "components/common/tabbar/TabBarItem";

export default {
  name: "MainTabBar",
  components: {
    TabBar,
    TabBarItem,
  },
  data() {
    return {};
  },
};
</script>

<style lang="sass" scoped>
</style>