<template>
  <div :class="{notification: true, notice: type === 'notice', danger: type === 'danger'}">
    <div class="message">{{message}}</div>
    <div @click="e=>onRemove(id)" class="remove">+</div>
  </div>
</template>

<script>
export default {
  name: "Alert",
  props: {
    type: {
      type: String,
      default: "notice"
    },
    message: {
      type: String,
      default: ""
    },
    onRemove: {
      type: Function,
      default: () => null
    },
    id: {
      type: Number
    }
  }
};
</script>

<style scoped lang="scss">
@import "../../variables/variables.scss";
.notification {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 5px;
  width: auto;
  height: 40px;
  padding: 0 10px;
  position: relative;
  overflow: hidden;

  .remove {
    right: 0;
    width: 20px;
    height: 20px;
    transform: rotate(45deg);
    font-weight: bold;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 4px;
    font-size: 20px;
  }
}
.danger {
  border: 1px solid $danger-border;
  background-color: $danger-background;
  color: $danger-text;
}
.notice {
  border: 1px solid $notice-border;
  background-color: $notice-background;
  color: $notice-text;
}
</style>