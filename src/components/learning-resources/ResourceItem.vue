<template>
  <li class="resource">
    <base-card>
      <header class="resource__header">
        <h3 class="resource__title">{{ resource.title }}</h3>
        <base-button mode="button--flat" @click="deleteResource(resource.id)">Delete</base-button>
      </header>
      <p class="resource__description">{{ resource.description }}</p>
      <nav>
        <a class="resource__link" :href="resource.link">Learn more...</a>
      </nav>
    </base-card>
  </li>
</template>

<script>
export default {
  inject: ['deleteResource'],
  props: {
    resource: {
      type: Object,
    }
  }
};
</script>

<style lang="less" scoped>
@import '../../variables.less';

.resource {
  margin: auto;
  max-width: 40rem;

  .resource__header {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .resource__title {
      font-size: 1.25rem;
      margin: 0.5rem 0;
    }
  }

  .resource__link {
    text-decoration: none;
    color: @color-dynamic;
    font-weight: 600;

    &.resource__link:hover,
    &.resource__link:active {
      color: @color-dynamic-light;
    }
  }

  .resource__description {
    margin: 0.5rem 0;
  }
}
</style>