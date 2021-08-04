<template>
  <button :class="mode">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    mode: {
      type: String,
      default: ''
    }
  }
};
</script>

<style lang="less" scoped>
@import '../../variables.less';

button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: @color-primary;
  border: 1px solid @color-primary;
  color: white;
  cursor: pointer;
  & button:hover,
  & button:active {
    background-color: @color-primary-dark;
    border-color: @color-primary-dark;
  }
}

.button--flat {
  background-color: transparent;
  color: @color-primary;
  border: none;
  &.butoon--flat:active,
  &.button--flat:hover {
    background-color: @color-primary-light;
  }
}
</style>