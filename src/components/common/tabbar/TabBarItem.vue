<template>
  <div class="tab" :class="{ active: isActive }" @click="itemClick()">
    <slot name="icon"></slot>
    <slot name="text"></slot>
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props:{
    path:String
  },
  data() {
    return {
      isActive: false,
    };
  },
  methods:{
    itemClick(){
      this.$router.replace(this.path)
    }
  }
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

  &.active {
    color: rgb(0, 135, 220);
  }

  img {
    width: 24px;
    height: 24px;
    margin-top: 2px;
    opacity: .75;
  }

  span {
    width: 100%;
    text-align: center;
    font-size: 14px;
    color: inherit;
  }
}
</style>