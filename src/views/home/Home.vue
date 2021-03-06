<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template #center>首页</template>
    </nav-bar>
    <tab-control
      class="home-tab"
      :titles="['流行', '新款', '精选']"
      @tabClick="tabClick"
      ref="tabbarFixed"
      v-show="isCeiling"
    />
    <scroll
      class="home-body"
      ref="scroll"
      :probe-type="3"
      @scrollPosition="contentScroll"
      :pull-up-load="true"
      @scrollUpload="contentLoad"
    >
      <home-swiper :banners="banners" @swiperImageLoaded="swiperImageLoaded" />
      <recommend-view :recommends="recommends" />
      <feature-view />
      <tab-control
        :titles="['流行', '新款', '精选']"
        @tabClick="tabClick"
        ref="tabbar"
      />
      <goods-list :goods="showGoods" />
    </scroll>
    <!-- native修饰符在组件事件监听时使用 -->
    <back-top @click.native="backTop" v-show="isBackTop" />
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
import BackTop from "components/content/backTop/BackTop";

import { getHomeMultidata, getHomeGoods } from "network/home";

import { debounce } from "common/utils";

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
    BackTop,
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
              image: "assets/img/home/clothing.jpeg",
              title: "流行商品名称1",
              price: "￥100.00",
              collect: "50",
              iid:"2lkjdls"
            },
            {
              image: "assets/img/home/clothing.jpeg",
              title: "流行商品名称2",
              price: "￥120.00",
              collect: "32",
              iid:"askdfjoi"
            },
            {
              image: "assets/img/home/clothing.jpeg",
              title:
                "流行testtesttesttesttesttesttesttesttesttesttesttesttesttest",
              price: "￥1200.00",
              collect: "1",
              iid:"cl9vmld"
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
              iid:"qpdalkf"
            },
            {
              image: "assets/logo.png",
              title: "新款商品名称2",
              price: "￥150.00",
              collect: "20",
              iid:"5fqa52a1d"
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
              iid:"4eopfka"
            },
            {
              image: "assets/logo.png",
              title: "热销商品名称2",
              price: "￥10.00",
              collect: "1002",
              iid:"p[akdfld"
            },
            {
              image: "assets/logo.png",
              title: "热销商品名称3",
              price: "￥10.00",
              collect: "1002",
              iid:"sdfklja"
            },
            {
              image: "assets/logo.png",
              title: "热销商品名称4",
              price: "￥10.00",
              collect: "1002",
              iid:"aemfsdf"
            },
            {
              image: "assets/logo.png",
              title: "热销商品名称5",
              price: "￥10.00",
              collect: "1002",
              iid:"piqwfd"
            },
          ],
        },
      },
      currentType: "pop",
      isBackTop: false,
      tabPosTop: 0,
      isCeiling: false,
      saveY: 0,
    };
  },
  computed: {
    showGoods() {
      return this.fakeGoods[this.currentType].list;
    },
  },
  created() {
    // 请求轮播图数据
    this.getHomeMultidataFn();

    // 请求商品数据
    this.getHomeGoodsFn("pop");
    this.getHomeGoodsFn("news");
    this.getHomeGoodsFn("sell");
  },
  mounted() {
    //事件总线监听
    //防抖函数-提高性能
    const refresh = debounce(this.$refs.scroll.refresh, 50);
    this.$bus.$on("imageLoaded", () => {
      refresh();
    });
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
          this.$refs.scroll.finishPullUp();
        })
        .catch((err) => {
          console.log("数据获取失败");
          this.$refs.scroll.finishPullUp();
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
      this.$refs.tabbar.currentIndex = index;
      this.$refs.tabbarFixed.currentIndex = index;
    },
    backTop() {
      this.$refs.scroll.backTop(0, 0);
    },
    contentScroll(position) {
      this.isBackTop = position.y < -300 ? true : false;
      this.isCeiling = this.tabPosTop < -position.y;
    },
    contentLoad() {
      this.getHomeGoodsFn(this.currentType);
    },
    swiperImageLoaded() {
      this.$refs.scroll.refresh();
      //$el获取组件中的元素
      this.tabPosTop = this.$refs.tabbar.$el.offsetTop - 44;
    },
  },
  activated() {
    this.$refs.scroll.backTop(0, this.saveY, 0);
    this.$refs.scroll.refresh();
  },
  deactivated() {
    this.saveY = this.$refs.scroll.getScrollY();
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

  .home-tab {
    background: #fff;
    position: absolute;
    z-index: 50;
    top: 44px;
  }

  .home-body {
    width: 100%;
    height: calc(100% - 44px);
  }
}
</style>