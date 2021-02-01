<template>
  <div class="goods">
    <img :src="goodsItem.image" alt="" />
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
};
</script>

<style lang="scss" scoped>
.goods {
  width: 50%;
  float: left;
  padding: 5px;

  img {
    width: 100%;
    height: 250px;
    background: #eee;
    float: left;
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
    float: left;
  }

  b {
    color: #000;
    font-weight: bold;
  }

  span{
    color: rgba(0,0,0,.75);
  }
}
</style>