<template>
  <tab-bar>
    <tab-bar-item path="/home" activeColor="deepPick">
      <template #icon>
        <img src="assets/img/tabbar/tab01.svg" alt="" />
      </template>
      <template #text>
        <span>首页</span>
      </template>
    </tab-bar-item>
    <tab-bar-item path="/category" activeColor="deepPick">
      <template #icon>
        <img src="assets/img/tabbar/tab02.svg" alt="" />
      </template>
      <template #text>
        <span>分类</span>
      </template>
    </tab-bar-item>
    <tab-bar-item path="/cart" activeColor="deepPick">
      <template #icon>
        <img src="assets/img/tabbar/tab03.svg" alt="" />
      </template>
      <template #text>
        <span>购物车</span>
      </template>
    </tab-bar-item>
    <tab-bar-item path="/profile" activeColor="deepPick">
      <template #icon>
        <img src="assets/img/tabbar/tab04.svg" alt="" />
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
    return {
      navi: [
        {
          icon: "assets/img/tabbar/tab01.svg",
          text: "首页",
        },
        {
          icon: "assets/img/tabbar/tab02.svg",
          text: "分类",
        },
        {
          icon: "assets/img/tabbar/tab03.svg",
          text: "购物车",
        },
        {
          icon: "assets/img/tabbar/tab04.svg",
          text: "我的",
        },
      ],
    };
  },
};
</script>

<style lang="sass" scoped>
</style>