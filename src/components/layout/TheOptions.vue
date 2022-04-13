<template>
  <div class="container text-center options-wrapper">
    <BaseButton
      class="me-4"
      :class="activeButton == 'TheResources' ? 'active' : ''"
      @click="optionToggler('TheResources')"
      >Stored Resources
    </BaseButton>
    <BaseButton
      :class="activeButton == 'TheForm' ? 'active' : ''"
      @click="optionToggler('TheForm')"
      >New Resource</BaseButton
    >
  </div>
</template>

<script>
import BaseButton from "../UI/BaseButton.vue";

export default {
  props: ["redirectActiveButton"],
  data() {
    return {
      activeButton: "TheResources",
    };
  },
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
  watch: {
    redirectActiveButton() {
      if (this.redirectActiveButton) {
        this.activeButton = this.redirectActiveButton;
      }
    },
  },
  components: {
    BaseButton,
  },
  methods: {
    optionToggler(compName) {
      this.activeButton = compName;
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
