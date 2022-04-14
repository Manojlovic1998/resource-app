<template>
  <div class="row base-card">
    <div class="col-12">
      <slot name="title"></slot>
    </div>
    <div class="col-12">
      <slot name="body"></slot>
    </div>
    <div class="col-12">
      <BaseTag>
        <slot name="tag"></slot>
      </BaseTag>
    </div>
    <div class="col-12 d-flex">
      <slot name="resource"></slot>
      <slot name="delete"></slot>
    </div>
  </div>
</template>

<script>
import BaseTag from "./BaseTag.vue";

export default {
  components: {
    BaseTag,
  },
};
</script>

<style scoped>
.base-card {
  background-color: #ffffff;
  padding: 16px;
  filter: drop-shadow(0px 1px 1px rgba(0, 0, 0, 0.25));
  border-radius: 5px;
}
</style>