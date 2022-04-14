<template>
  <div class="container mt-5 pb-5">
    <div class="col-12 col-md-10 col-lg-6 mx-md-auto">
      <form
        class="form-wrapper d-flex flex-column"
        @submit.prevent="addNewResource"
      >
        <div class="form-heading mx-md-auto">
          <h2 class="mb-5 fw-bold">New Resource</h2>
        </div>
        <div class="form-group mx-md-auto">
          <label for="title" class="fw-bold text-gray d-block">Title</label>
          <input
            class="mt-2"
            ref="title"
            type="text"
            name="title"
            id="title"
            required
          />
        </div>
        <div class="form-group mt-3 mx-md-auto">
          <label for="body" class="fw-bold text-gray d-block"
            >Description</label
          >
          <textarea
            class="mt-2"
            name="body"
            id="body"
            cols="50"
            rows="4"
            ref="body"
            required
          ></textarea>
        </div>
        <div class="form-group mx-md-auto">
          <label for="resource" class="fw-bold text-gray d-block"
            >Resource URL</label
          >
          <input
            class="mt-2"
            ref="resource"
            type="url"
            name="resource"
            id="resource"
            required
          />
        </div>
        <div class="form-group mt-2 mx-md-auto tag-group">
          <label for="tag" class="fw-bold text-gray d-block">Type</label>
          <select name="tag" id="tag" class="mt-2" ref="tag">
            <option value="Plugin">Plugin</option>
            <option value="Language">Language</option>
            <option value="Design">Design</option>
            <option value="Framework">Framework</option>
          </select>
        </div>
        <div class="button-wrapper mx-md-auto mt-5">
          <BaseButton class="active">Add Resource</BaseButton>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import BaseButton from "../UI/BaseButton.vue";

export default {
  props: ["resources"],
  emits: ["new-resource"],
  components: {
    BaseButton,
  },
  data() {
    return {};
  },
  methods: {
    addNewResource() {
      let id = !(this.resources[0] === undefined)
        ? this.resources[0].id + 1
        : 1;

      let resource = {
        // Not the best solution for the id
        // normaly you would use a hash algo to hash the data
        // sometimes even algo with some salt
        // for the sake of portfolio project it is good enough :)
        id,
        title: this.$refs.title.value,
        body: this.$refs.body.value,
        tag: this.$refs.tag.value,
        resource: this.$refs.resource.value,
      };

      this.$emit("new-resource", resource);

      this.$refs.title.value = "";
      this.$refs.body.value = "";
      this.$refs.tag.value = "";
      this.$refs.resource.value = "";
    },
  },
};
</script>

<style scoped>
.form-wrapper {
  background-color: #ffffff;
  border-radius: 10px;
  padding: 34px 21px;
  filter: drop-shadow(0px 1px 1px rgba(0, 0, 0, 0.25));
}

input {
  max-width: 300px;
  width: 100%;
}

input,
textarea,
select {
  border: 2px solid rgba(4, 9, 33, 0.32);
  border-radius: 8px;
}

textarea {
  width: 100%;
  max-width: 300px;
}

@media (min-width: 992px) {
  input,
  textarea,
  select {
    max-width: 400px;
  }

  #title,
  #resource {
    width: 300px;
  }

  #body {
    width: 300px;
  }

  .form-heading {
    width: 350px;
  }

  .button-wrapper {
    width: 300px;
  }

  .tag-group {
    width: 300px;
  }
}

label {
  color: #0f0f0f;
}

#title,
#resource {
  padding: 5px 8px;
}

#tag {
  width: 140px;
  text-align: center;
  padding: 5px 8px;
  background-color: #ffffff;
}

option {
  color: #0f0f0f;
  font-weight: 600;
}
</style>
