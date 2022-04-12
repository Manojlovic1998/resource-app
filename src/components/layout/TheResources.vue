<template>
  <div class="container resources-wrapper">
    <BaseCard v-for="resource in resources" :key="resource.id">
      <template v-slot:title
        ><p class="fw-bolder">{{ resource.title }}</p></template
      >
      <template v-slot:body
        ><p class="text-gray">{{ resource.body }}</p></template
      >
      <template v-slot:tag
        ><p class="mb-0 tag">{{ resource.tag }}</p></template
      >
      <template v-slot:resource
        ><a :href="resource.resource" class="fw-bold"
          >View Resource</a
        ></template
      >
    </BaseCard>
  </div>
</template>

<script>
import BaseCard from "../UI/BaseCard.vue";

export default {
  props: ["resources"],
  components: {
    BaseCard,
  },
};
</script>

<style scoped>
.resources-wrapper {
  margin-top: 52px;
}

.tag {
  color: #686868;
  font-weight: 600;
}

a {
  text-decoration: none;
}
</style>