<template>
  <div class="container text-center options-wrapper">
    <BaseButton class="me-4 active" @click="optionToggler('TheResources')"
      >Stored Resources
    </BaseButton>
    <BaseButton @click="optionToggler('TheForm')">New Resource</BaseButton>
  </div>
</template>

<script>
import BaseButton from "../UI/BaseButton.vue";

export default {
  emits: {
    "set-main": (compName) => {
      if (compName === "TheResources") {
        return true;
      } else if (compName === "TheForm") {
        return true;
      } else if (typeof compName !== "string") {
        console.warn("Component should be a string!");
        return false;
      }
    },
  },
  components: {
    BaseButton,
  },
  methods: {
    optionToggler(compName) {
      this.$emit("set-main", compName);
    },
  },
};
</script>

<style>
.options-wrapper {
  margin-top: 34px;
}
</style>
