<template>
  <div id="app">
    <Form @formAdd="addForm" />
    <TotalBalance :list="list" />
    <BudgetList :list="list" @deleteItem="onDeleteItem" />
  </div>
</template>

<script>
import BudgetList from "@/components/budgetList";
import TotalBalance from "@/components/TotalBalans";
import Form from "@/components/Form";

export default {
  name: "app",
  components: {
    BudgetList,
    TotalBalance,
    Form,
  },
  data: () => ({
    list: {},
  }),
  methods: {
    onDeleteItem(id) {
      this.$delete(this.list, id);
    },
    addForm(data) {
      const newObj = {
        ...data,
        id: String(Math.random()),
      };
      console.log(this.list.length);
      this.$set(this.list, newObj.id, newObj);
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
