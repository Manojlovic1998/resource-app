<template>
  <div class="container text-center options-wrapper">
    <BaseButton class="me-4 active">Stored Resources </BaseButton>
    <BaseButton>Add Resource </BaseButton>
  </div>
</template>

<script>
import BaseButton from "../UI/BaseButton.vue";

export default {
  components: {
    BaseButton,
  },
};
</script>

<style>
.options-wrapper {
  margin-top: 34px;
}
</style>