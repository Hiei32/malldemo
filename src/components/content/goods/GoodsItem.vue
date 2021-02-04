<template>
  <div class="goods" @click="itemClick">
    <img src="~assets/img/home/clothing.jpeg" alt="" @load="imageLoad" />
    <!-- <img :src="goodsItem.image" alt="" /> -->
    <b>{{ goodsItem.title }}</b>
    <span>{{ goodsItem.price }} - 收藏：{{ goodsItem.collect }}</span>
  </div>
</template>

<script>
export default {
  name: "GoodsItem",
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  methods: {
    imageLoad() {
      //事件总线发射
      this.$bus.$emit("imageLoaded");
    },
    itemClick() {
      this.$router.push("/detail/" + this.goodsItem.iid);
    },
  },
};
</script>

<style lang="scss" scoped>
.goods {
  width: 50%;
  padding: 5px;

  img {
    width: 100%;
    background: #eee;
  }

  b,
  span {
    width: 100%;
    height: 20px;
    line-height: 20px;
    text-align: left;
    display: inline-block;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  b {
    color: #000;
    font-weight: bold;
  }

  span {
    color: #666;
  }
}
</style>