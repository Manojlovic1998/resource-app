<template>
  <TheHeader />
  <TheMain>
    <BaseHero>
      <h1>Welcome back, Nemanja</h1>
      <p class="text-gray mb-0 sub-hero-heading">
        You've got {{ resources.length }} resources saved.
      </p>
    </BaseHero>
    <TheOptions
      @set-main="setMainComponent"
      :redirectActiveButton="mainComponent"
    />
    <keep-alive>
      <component
        :is="mainComponent"
        :resources="resources"
        @new-resource="addNewResource"
        @toggle-modal="toggleModal"
      ></component>
    </keep-alive>
    <!-- <TheResources :resources="resources" /> -->
  </TheMain>
  <BaseModal v-if="showModal">
    <template v-slot:title
      ><p class="fs-4 fw-bold mb-0">Confirm Action</p></template
    >
    <template v-slot:body
      ><p>
        Are you sure you want to delete
        <strong>{{ modalData.title }}</strong
        >?
      </p></template
    >
    <template v-slot:actions
      ><BaseButton
        class="me-3 btn-sm active"
        @click="toggleModal({ modalStatus: false })"
        >Cancel</BaseButton
      ><BaseButton
        class="me-3 btn-sm btn-danger"
        @click="deleteResource(modalData)"
        >Delete</BaseButton
      ></template
    >
  </BaseModal>
  <Teleport to="body">
    <BasePageOverlay
      v-if="showModal"
      @click="toggleModal({ modalStatus: false })"
      class="overlay"
    />
  </Teleport>
</template>

<script>
import TheHeader from "./components/layout/TheHeader.vue";
import BaseHero from "./components/UI/BaseHero.vue";
import TheMain from "./components/layout/TheMain.vue";
import TheOptions from "./components/layout/TheOptions.vue";
import TheResources from "./components/layout/TheResources.vue";
import TheForm from "./components/layout/TheForm.vue";
import BaseModal from "./components/UI/BaseModal.vue";
import BaseButton from "./components/UI/BaseButton.vue";
import BasePageOverlay from "./components/UI/BasePageOverlay.vue";

export default {
  components: {
    TheHeader,
    BaseHero,
    TheMain,
    TheOptions,
    TheResources,
    TheForm,
    BaseModal,
    BaseButton,
    BasePageOverlay,
  },
  data() {
    return {
      resources: [
        {
          id: 2,
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
      mainComponent: "TheResources",
      showModal: false,
      modalData: {
        title: "",
        body: "",
        tag: "",
      },
    };
  },
  methods: {
    setMainComponent(compName) {
      this.mainComponent = compName;
    },
    addNewResource(resource) {
      this.resources.push(resource);
      this.setMainComponent("TheResources");
    },
    toggleModal(modalData) {
      if (!modalData.resource) {
        this.showModal = modalData.modalStatus;
      } else {
        this.showModal = modalData.modalStatus;
        this.modalData = modalData.resource;
      }
    },
    deleteResource(modalData) {
      this.resources = this.resources.filter((el) => el.id != modalData.id);
      this.toggleModal({ modalStatus: false });
    },
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

<style scoped>
.btn-danger {
  background-color: #c74940;
}

.btn-danger:hover {
  background-color: #dd5147;
}
</style>
