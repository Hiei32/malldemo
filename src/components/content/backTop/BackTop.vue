<template>
  <div class="back-top"></div>
</template>

<script>
export default {
  name: "BackTop",
};
</script>

<style lang="scss" scoped>
.back-top {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: #fff;
  box-shadow: 0 0 2px rgba(0, 0, 0, 0.25);
  position: fixed;
  bottom: 60px;
  right: 10px;

  &:active {
    background: #eee;
  }

  &:before {
    content: "";
    width: 10px;
    height: 10px;
    border-top: 3px solid deeppink;
    border-left: 3px solid deeppink;
    transform: rotate(45deg);
    position: absolute;
    top: 50%;
    left: 50%;
    margin: -4px -6px;
  }
}
</style>