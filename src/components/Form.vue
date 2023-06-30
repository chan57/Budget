<template>
  <div class="form" @keydown.enter="op">
    <h6>Type</h6>
    <select
      class="form-select"
      v-model="formData.type"
      aria-label="Default select example"
    >
      <option value="INCOME">INCOME</option>
      <option value="OUTCOME">OUTCOME</option>
    </select>

    <div class="mb-3">
      <label for="Input3" class="form-label">Value</label>
      <input
        type="value"
        v-model.number="formData.value"
        class="form-control"
        id="value"
        placeholder="value"
      />
    </div>

    <div class="mb-3">
      <label for="Input2" class="form-label">Add comment</label>
      <input
        type="comment"
        class="form-control"
        id="comment"
        placeholder="comemnt"
        v-model="formData.comment"
      />
    </div>

    <button class="btn btn-secondary" @click="op">submit</button>
  </div>
</template>

<script>
export default {
  name: "Form",
  data: () => ({
    formData: {
      type: "INCOME",
      comment: "",
      value: "",
    },
  }),
  methods: {
    op() {
      if (this.formData.comment !== "" || this.formData.value !== "") {
        this.$emit("formAdd", this.formData);
        this.formData.comment = "";
        this.formData.value = "";
      } else console.log("vvedite danie");
    },
  },
};
</script>

<style scoped>
.form {
  max-width: 500px;
  margin: auto;
}

.form-select {
  padding: 18px;
}
</style>
