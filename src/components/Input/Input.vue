<template>
  <div>
    <input
      @change="onChange"
      :value="value"
      :placeholder="placeholder"
      :class="{input: true, error}"
      :type="type"
    />
  </div>
</template>

<script>
export default {
  name: "Input",
  props: {
    error: {
      type: Boolean,
      default: false
    },
    type: {
      type: String,
      default: "text"
    },
    placeholder: {
      type: String,
      default: ""
    },
    value: {
      type: String,
      default: ""
    },
    onChange: {
      type: Function,
      default: () => null
    }
  }
};
</script>

<style scoped lang="scss">
@import "../../variables/variables.scss";
.input {
  height: 30px;
  width: 100%;
  box-sizing: border-box;
  outline: none;
  padding: 3px;
  margin: 5px 1px 3px 0px;
  border: 1px solid $input-border-color;
  border-radius: 3px;
  &:focus {
    box-shadow: 0 0 5px $input-foused-box-shadow-color;
    padding: 3px;
    margin: 5px 1px 3px 0px;
    border: 1px solid $input-foused-border-color;
  }
}
.error {
  border: 1px solid $input-error-foused-border-color;
  box-shadow: 0 0 5px $input-error-box-shadow-color;
}
</style>