<template>
  <div :class="{notification: true, notice: type === 'notice', danger: type === 'danger'}">
    {{message}}
    <div @click="e=>onRemove(id)" class="remove">+</div>
  </div>
</template>

<script>
export default {
  name: "Alert",
  props: {
    type: {
      type: String,
      default: 'notice'
    },
    message: {
      type: String,
      default: ''
    },
    onRemove: {
      type: Function,
      default: ()=>null
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
  align-items: center;
  border-radius: 5px;
  width: auto;
  height: 40px;
  padding: 0 20px;
  position: relative;
  overflow: hidden;
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
.remove {
  position: absolute;
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
</style>