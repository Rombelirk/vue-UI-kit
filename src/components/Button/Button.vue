<template>
  <div :class="{button: true, disabled}" @click="click">
    <slot />
  </div>
</template>

<script>
export default {
  name: "Button",
  methods: {
    click() {
      if (this.disabled) {
        return false;
      }
      this.onClick();
    }
  },
  props: {
    onClick: {
      type: Function,
      default: e => null
    },
    disabled: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style scoped lang="scss">
@import "../../variables/variables.scss";
.button {
  height: 20px;
  padding: 10px 20px;
  border-radius: 5px;
  border: 1px solid $button-border-color;
  background-color: $button-background-color;
  color: $button-color;
  cursor: pointer;
  max-width: fit-content;
  transition: 300ms;
  &:hover {
    background-color: $button-hover-background-color;
  }
}

.disabled {
  color: $button-color;
  background-color: $disabled-button-background-color;
  border-color: $disabled-button-border-color;
  cursor: auto;
  &:hover {
    color: $button-color;
    background-color: $disabled-button-background-color;
    border-color: $disabled-button-border-color;
  }
}
</style>