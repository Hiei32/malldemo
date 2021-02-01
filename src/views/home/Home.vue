<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template #center>首页</template>
    </nav-bar>
    <home-swiper :banners="banners" />
    <recommend-view :recommends="recommends" />
    <feature-view />
    <tab-control class="tab-control" :titles="['流行', '新款', '精选']" />
    <goods-list :goods="fakeGoods" />

    <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
    <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
    <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
  </div>
</template>

<script>
import HomeSwiper from "./childComps/HomeSwiper";
import RecommendView from "./childComps/RecommendView";
import FeatureView from "./childComps/FeatureView";

import NavBar from "components/common/navbar/NavBar";
import TabControl from "components/content/tabControl/TabControl";
import GoodsList from "components/content/goods/GoodsList";

import { getHomeMultidata, getHomeGoods } from "network/home";

export default {
  name: "Home",
  components: {
    HomeSwiper,
    RecommendView,
    FeatureView,
    NavBar,
    TabControl,
    GoodsList,
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        pop: {
          page: 0,
          list: [],
        },
        news: {
          page: 0,
          list: [],
        },
        sell: {
          page: 0,
          list: [],
        },
      },
      fakeGoods: [
        {
          image: "assets/logo.png",
          title: "商品名称1",
          price: "￥100.00",
          collect: "50",
        },
        {
          image: "assets/logo.png",
          title: "商品名称2",
          price: "￥120.00",
          collect: "32",
        },
        {
          image: "assets/logo.png",
          title: "testtesttesttesttesttesttesttesttesttesttesttesttesttest",
          price: "￥1200.00",
          collect: "1",
        },
      ],
    };
  },
  created() {
    // 请求轮播图数据
    this.getHomeMultidataFn();

    // 请求商品数据
    this.getHomeGoodsFn("pop");
    this.getHomeGoodsFn("news");
    this.getHomeGoodsFn("sell");
  },
  methods: {
    getHomeMultidataFn() {
      getHomeMultidata().then((res) => {
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      });
    },
    getHomeGoodsFn(type) {
      const page = this.goods[type].page + 1;
      getHomeGoods(type, page)
        .then((res) => {
          this.goods[type].list.push(...res.data.list);
          this.goods[type].page += 1;
        })
        .catch((err) => {
          console.log("数据获取失败");
        });
    },
  },
};
</script>

<style lang="scss" scoped>
#home {
  padding-top: 44px;
}

.home-nav {
  background: deeppink;
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  z-index: 10;
}

.tab-control {
  position: sticky;
  top: 44px;
  background: #fff;
}
</style>