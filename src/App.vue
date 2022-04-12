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
    <TheResources :resources="resources" />
  </TheMain>
</template>

<script>
import TheHeader from "./components/layout/TheHeader.vue";
import BaseHero from "./components/UI/BaseHero.vue";
import TheMain from "./components/layout/TheMain.vue";
import TheOptions from "./components/layout/TheOptions.vue";
import TheResources from "./components/layout/TheResources.vue";

export default {
  components: {
    TheHeader,
    BaseHero,
    TheMain,
    TheOptions,
    TheResources,
  },
  data() {
    return {
      resources: [
        {
          id: 1,
          title: "Vetur Vue Plugin",
          body: "Vetur is Vue plugin that helps with linting of vue files.",
          tag: "Framework",
          resource: "https://github.com/vuejs/vetur",
        },
        {
          id: 1,
          title: "Vetur Vue Plugin",
          body: "Vetur is Vue plugin that helps with linting of vue files.",
          tag: "Framework",
          resource: "https://github.com/vuejs/vetur",
        },
      ],
    };
  },
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
