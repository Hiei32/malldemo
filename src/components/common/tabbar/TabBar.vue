<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "TabBar",
};
</script>

<style scoped>
#tab-bar {
  width: 100%;
  height: 49px;
  background: #f4f4f4;
  position: fixed;
  right: 0;
  bottom: 0;
  left: 0;
  display: flex;
  box-shadow: 0 -1px 0 rgba(0, 0, 0, 0.1);
}
</style>
