<template>
  <div @click="toggle" :class="{switch: true, 'switch-toggled':toggled}">
    <div :class="{slider: true, 'slider-toggled':toggled}"></div>
  </div>
</template>

<script>
export default {
  name: "Switch",
  props: {
    defaultToggle: false
  },
  props: {
    toggleProp: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {
      toggled: this.toggleProp || false
    };
  },
  methods: {
    toggle() {
      this.toggled = !this.toggled;
    }
  }
};
</script>

<style scoped lang="scss">
.switch {
  height: 14px;
  width: 35px;
  background-color: #9c9c9c;
  cursor: pointer;
  border-radius: 500px;
  display: flex;
  align-items: center;
  position: relative;
  transition: 200ms ease-out;
  .slider {
    position: absolute;
    border-radius: 50%;
    background-color: rgb(221, 221, 221);
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
  background-color: #acc289;
}
</style>