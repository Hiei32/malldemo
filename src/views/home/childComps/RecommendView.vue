<template>
  <div class="recommends">
    <a
      href=""
      v-for="(item, index) in recommends"
      :key="index"
      :src="item.link"
    >
      <img :src="item.image" alt="" />
      <span>{{ item.title }}</span>
    </a>
  </div>
</template>

<script>
export default {
  name: "RecommendView",
  props: {
    recommends: {
      type: Array,
      default() {
        return [];
      },
    },
  },
};
</script>

<style lang="scss" scoped>
.recommends {
  width: 100%;
  display: flex;
  justify-content: space-around;
  padding: 10px 0;
  margin-bottom: 10px;

  a {
    flex: 1;
    text-align: center;

    img {
      width: 64px;
      height: 64px;
      margin-bottom: 4px;
    }

    span {
      width: 100%;
      height: 20px;
      line-height: 20px;
      text-align: center;
      display: inline-block;
      font-size: 14px;
    }
  }
}
</style>