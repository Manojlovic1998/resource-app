<template>
  <div class="container resources-wrapper pb-4">
    <BaseCard class="mt-4" v-for="resource in resources" :key="resource.id">
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
        ><a :href="resource.resource" target="_blank" class="fw-bold"
          >View Resource</a
        ></template
      >
      <template v-slot:delete
        ><BaseButton class="btn-sm ms-auto">Delete</BaseButton></template
      >
    </BaseCard>
  </div>
</template>

<script>
import BaseCard from "../UI/BaseCard.vue";
import BaseButton from "../UI/BaseButton.vue";

export default {
  props: ["resources"],
  components: {
    BaseCard,
    BaseButton,
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

.btn-sm {
  background-color: #dd5147;
}

.btn-sm:hover {
  background-color: #c74940;
}

a {
  text-decoration: none;
}
</style>