<template>
  <TheHeader />
  <TheMain>
    <BaseHero>
      <h1>Welcome back, Nemanja</h1>
      <p class="text-gray mb-0 sub-hero-heading">
        You've got ... resources saved.
      </p>
    </BaseHero>
    <TheOptions />
  </TheMain>
</template>

<script>
import TheHeader from "./components/layout/TheHeader.vue";
import BaseHero from "./components/UI/BaseHero.vue";
import TheMain from "./components/layout/TheMain.vue";
import TheOptions from "./components/layout/TheOptions.vue";

export default {
  components: {
    TheHeader,
    BaseHero,
    TheMain,
    TheOptions,
  },
  data() {},
};
</script>

<style>
html,
body {
  background-color: #f6f6f6;
}

.sub-hero-heading {
  margin-top: 21px;
  font-weight: 700;
}

p,
h1,
h2,
h3 {
  color: #0f0f0f;
}

.text-gray {
  color: #828282;
}
</style>
