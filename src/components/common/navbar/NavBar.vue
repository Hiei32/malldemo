<template>
  <div class="nav-bar">
    <div class="nav-left">
      <slot name="left"></slot>
    </div>
    <div class="nav-center">
      <slot name="center"></slot>
    </div>
    <div class="nav-right">
      <slot name="right"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "NavBar",
};
</script>

<style lang='scss' scoped>
.nav-bar {
  min-height: 44px;
  display: flex;
  color: #fff;
  box-shadow: 0 0 5px rgba(0,0,0,.1);

  .nav-left,
  .nav-right {
    min-width: 40px;
  }
  .nav-center {
    width: 1%;
    line-height: 44px;
    flex: 1;
    text-align: center;
    font-size: 17px;
    font-weight: bold;

    &:first-child {
      margin-left: 40px;
    }

    &:last-child {
      margin-right: 40px;
    }
  }
}
</style>