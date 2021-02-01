<template>
  <div class="goods-list">
    <goods-item
      v-for="(item, index) in goods"
      :key="index"
      :goods-item="item"
    />
  </div>
</template>

<script>
import GoodsItem from "./GoodsItem";
export default {
  name: "GoodsList",
  components: {
    GoodsItem,
  },
  props: {
    goods: {
      type: Array,
      default() {
        return [];
      },
    },
  },
};
</script>

<style lang="scss" scoped>
.goods-list {
  width: 100%;
  padding: 5px;
  font-size: 14px;
}
</style>