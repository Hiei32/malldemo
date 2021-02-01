<template>
  <div class="tab-control">
    <div
      v-for="(item, index) in titles"
      :key="index"
      class="tab-control-item"
      :class="{ active: index === currentIndex }"
      @click="tabClick(index)"
    >
      <span>{{ item }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabControl",
  props: {
    titles: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data() {
    return {
      currentIndex: 0,
    };
  },
  methods: {
    tabClick(index) {
      this.currentIndex = index;
    },
  },
};
</script>

<style lang="scss" scoped>
.tab-control {
  width: 100%;
  display: flex;
  text-align: center;

  .tab-control-item {
    flex: 1;
    padding: 4px 0;

    span {
      display: inline-block;
      font-size: 16px;
      padding: 6px 0;
    }

    &.active {
      span {
        color: deeppink;
        border-bottom: 2px solid deeppink;
      }
    }
  }
}
</style>