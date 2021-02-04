<template>
  <div class="detail-navbar">
    <nav-bar>
      <template #left>
        <div class="return" @click="backClick"></div>
      </template>
      <template #center>
        <div class="detail-nav-group">
          <div
            class="detail-nav"
            :class="{ active: index == currentIndex }"
            v-for="(item, index) in titles"
            :key="index"
            @click="navChoose(index)"
          >
            {{ item }}
          </div>
        </div>
      </template>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";

export default {
  name: "DetailNavBar",
  components: {
    NavBar,
  },
  data() {
    return {
      titles: ["商品", "参数", "评论", "推荐"],
      currentIndex: 0,
    };
  },
  methods: {
    navChoose(index) {
      this.currentIndex = index;
    },
    backClick() {
      this.$router.back();
    },
  },
};
</script>

<style lang="scss" scoped>
.detail-navbar {
  .return {
    width: 40px;
    height: 44px;
    display: flex;
    justify-content: center;
    align-items: center;

    &:before {
      content: "";
      width: 12px;
      height: 12px;
      border-top: 3px solid #999;
      border-left: 3px solid #999;
      transform: rotate(-45deg);
    }

    &:active {
      &:before {
        border-color: deeppink;
      }
    }
  }

  .detail-nav-group {
    width: 100%;
    display: flex;
    justify-content: center;

    .detail-nav {
      line-height: 44px;
      height: 44px;
      color: #666;
      font-weight: normal;
      font-size: 14px;
      padding: 0 16px;

      &.active {
        color: deeppink;
      }
    }
  }
}
</style>