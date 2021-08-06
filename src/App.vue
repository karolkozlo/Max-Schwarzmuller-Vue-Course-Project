<template>
  <main>
    <the-header title="RememberMe"></the-header>
    <the-resources></the-resources>
  </main>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/learning-resources/TheResources.vue';
import './variables.less';

export default {
  components: {
    TheHeader,
    TheResources
  }
};
</script>

<style lang="less">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
@import './variables.less';


* {
  box-sizing: border-box;
}

html {
  font-family: @font-primary;

  body {
    margin: 0;
  }
}
</style>