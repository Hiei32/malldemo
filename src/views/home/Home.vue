<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template #center>首页</template>
    </nav-bar>
    <scroll class="home-body">
      <home-swiper :banners="banners" />
      <recommend-view :recommends="recommends" />
      <feature-view />
      <tab-control
        class="tab-control"
        :titles="['流行', '新款', '精选']"
        @tabClick="tabClick"
      />
      <goods-list :goods="showGoods" />
    </scroll>
  </div>
</template>

<script>
import HomeSwiper from "./childComps/HomeSwiper";
import RecommendView from "./childComps/RecommendView";
import FeatureView from "./childComps/FeatureView";

import Scroll from "components/common/scroll/Scroll";
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
    Scroll,
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
      fakeGoods: {
        pop: {
          page: 0,
          list: [
            {
              image: "assets/logo.png",
              title: "流行商品名称1",
              price: "￥100.00",
              collect: "50",
            },
            {
              image: "assets/logo.png",
              title: "流行商品名称2",
              price: "￥120.00",
              collect: "32",
            },
            {
              image: "assets/logo.png",
              title:
                "流行testtesttesttesttesttesttesttesttesttesttesttesttesttest",
              price: "￥1200.00",
              collect: "1",
            },
          ],
        },
        news: {
          page: 0,
          list: [
            {
              image: "assets/logo.png",
              title: "新款商品名称1",
              price: "￥140.00",
              collect: "12",
            },
            {
              image: "assets/logo.png",
              title: "新款商品名称2",
              price: "￥150.00",
              collect: "20",
            },
          ],
        },
        sell: {
          page: 0,
          list: [
            {
              image: "assets/logo.png",
              title: "热销商品名称1",
              price: "￥10.00",
              collect: "1002",
            },
          ],
        },
      },
      currentType: "pop",
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
  computed: {
    showGoods() {
      return this.fakeGoods[this.currentType].list;
    },
  },
  methods: {
    // 网络请求
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
    // 事件监听
    tabClick(index) {
      switch (index) {
        case 0:
          this.currentType = "pop";
          break;
        case 1:
          this.currentType = "news";
          break;
        case 2:
          this.currentType = "sell";
      }
    },
  },
};
</script>

<style lang="scss" scoped>
#home {
  width: 100%;
  height: calc(100vh - 50px);
  position: relative;

  .home-nav {
    background: deeppink;
  }

  .home-body {
    width: 100%;
    height: calc(100% - 44px);

    .tab-control {
      background: #fff;
    }
  }
}
</style>