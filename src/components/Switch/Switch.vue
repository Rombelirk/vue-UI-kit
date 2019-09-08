<template>
  <div @click="onToggle" :class="{switch: true, 'switch-toggled':toggled}">
    <div :class="{slider: true, 'slider-toggled':toggled}"></div>
  </div>
</template>

<script>
export default {
  name: "Switch",
  props: {
    toggleProp: {
      type: Boolean,
      default: true
    },
    onToggle: {
      type: Function,
      default: ()=>null
    },
    toggled: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style scoped lang="scss">
@import "../../variables/variables.scss";
.switch {
  height: 14px;
  width: 35px;
  background-color: $switch-background-color;
  cursor: pointer;
  border-radius: 500px;
  display: flex;
  align-items: center;
  position: relative;
  transition: 200ms ease-out;
  .slider {
    position: absolute;
    border-radius: 50%;
    background-color: $switch-slider-background-color;
    width: 20px;
    height: 20px;
    transition: 200ms ease-out;
  }
  .slider-toggled {
    transform: translate(15px);
    transition: 200ms ease-out;
  }
}
.switch-toggled {
  background-color: $switch-toggled-background-color;
}
</style>