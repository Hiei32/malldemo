<template>
  <div class="tab" :class="{ active: isActive }" @click="itemClick()">
    <slot name="icon"></slot>
    <slot name="text"></slot>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    path: String,
  },
  data() {
    return {};
  },
  methods: {
    itemClick() {
      if(this.$route.path.indexOf(this.path) === 0) return
      this.$router.push(this.path);
    },
  },
  computed: {
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1;
    },
  },
};
</script>

<style lang='scss'>
.tab {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: #000;

  img {
    width: 20px;
    height: 20px;
    margin: 2px 0 4px;
    opacity: 0.75;

    &.default-img {
      display: block;
    }
    &.active-img {
      display: none;
    }
  }

  &.active {
    color: deeppink;

    img {
      &.default-img {
        display: none;
      }
      &.active-img {
        display: block;
      }
    }
  }

  span {
    width: 100%;
    text-align: center;
    font-size: 14px;
    color: inherit;
  }
}
</style>