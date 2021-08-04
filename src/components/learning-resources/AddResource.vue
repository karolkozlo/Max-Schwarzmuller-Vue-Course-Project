<template>
  <!--Error Dialog Window -->
  <base-dialog v-if="!isInputValid" title="Invalid Input" @click="confirmError">
    <template #default>
      <p>Unfortunately, at least one input value is invalid</p>
      <p>Please, check your input values</p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Ok</base-button>
    </template>
  </base-dialog>
  <!--Error Dialog Window -->

  <base-card>
    <form @submit.prevent="submitData" class="form">
      <div class="form__control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleInput"/>
      </div>
      <div class="form__control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          ref="descriptionInput">
        </textarea>
      </div>
      <div class="form__control">
        <label for="link"></label>
        <input id="link" name="link" type="url" ref="linkInput"/>
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';

export default {
  components: { BaseButton },
  inject: ['addResource'],
  data() {
    return {
      isInputValid: true,
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescription = this.$refs.descriptionInput.value;
      const enteredLink = this.$refs.linkInput.value;
      if (enteredTitle.trim() === '' || enteredDescription.trim() === '' || enteredLink.trim() === '') {
        this.isInputValid = false;
        return;
      }
      this.addResource(enteredTitle, enteredDescription, enteredLink);
    },
    confirmError() {
      this.isInputValid = true;
    }
  }
};
</script>

<style lang="less">
@import '../../variables.less';

.form__control {
  margin: 1rem 0;

  label {
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
  }

  input,
  textarea {
    display: block;
    width: 100%;
    font: inherit;
    padding: 0.15rem;
    border: 1px solid #ccc;
  }

  input:focus,
  textarea:focus {
    outline: none;
    border-color: @color-primary;
    background-color: @color-primary-light;
  }
}
</style>