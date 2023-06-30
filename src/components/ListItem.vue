<template>
  <div>
    <h5 class="card-title">{{ obj.type }}</h5>
    <p class="card-textt">{{ obj.comment }}</p>
    <p class="card-text">{{ obj.value }}</p>
    <button @click="deleteI(obj.id)" class="btn btn-danger">delete</button>
    

  </div>
  
</template>

<script>
export default {
  name: "ListItem",
  props: {
    obj: {
      type: Object,
      default: () => ({}),
    },
  },
  methods: {
    deleteI(id) {
      this.$emit("del", id);
    },
  },
};
</script>

<style scoped>
button {
  width: 150px;
  margin: 0 auto;
  text-align: center;
  background-color: rgb(211, 169, 255);
  color: rgb(255, 255, 255);
  padding: 10px 20px;
  border-radius: 5px;
}
</style>
