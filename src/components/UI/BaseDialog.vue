<template>
  <div class="dialog-window" @click="$emit('close')">
    <dialog open>
      <header class="dialog-window__header">
        <slot name="header">
          <h2>{{ title }}</h2>
        </slot>
      </header>
      <section class="dialog-window__content">
        <slot></slot>
      </section>
      <menu class="dialog-window__actions">
        <slot name="actions">
          <base-button @click="$emit('close')">Close</base-button>
        </slot>
      </menu>
    </dialog>
  </div>
</template>

<script>
import BaseButton from './BaseButton.vue';

export default {
  components: { BaseButton },
  props: {
    title: {
      type: String,
      required: false
    }
  },
  emits: ['close']
};
</script>

<style lang="less" scoped>
@import '../../variables.less';
.dialog-window {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100%;
  background-color: @color-shadow;
  z-index: 10;

  dialog {
    position: fixed;
    top: 20vh;
    left: 10%;
    width: 80%;
    z-index: 100;
    border-radius: 12px;
    border: none;
    box-shadow: 0 2px 8px @color-shadow;
    padding: 0;
    margin: 0;
    overflow: hidden;

    .dialog-window__header {
      background-color: @color-primary;
      color: white;
      width: 100%;
      padding: 1rem;

      h2 {
        margin: 0;
      }
    }
    .dialog-window__content {
      padding: 1rem;
    }
    .dialog-window__actions {
      padding: 1rem;
      display: flex;
      justify-content: flex-end;
      margin: 0;
    }
  }
  @media (min-width: 768px) {
    dialog {
      left: calc(50% - 20rem);
      width: 40rem;
    }
  }
}
</style>