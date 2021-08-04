<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: {
    title: {
      type: String
    }
  }
};
</script>

<style lang="less" scoped>
@import '../../variables.less';

header {
  width: 100%;
  height: 5rem;
  background-color: @color-header;
  display: flex;
  justify-content: center;
  align-items: center;

  h1 {
    color: white;
    margin: 0;
  }
}
</style>