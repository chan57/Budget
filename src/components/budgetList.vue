<template>
  <div class="budget-list-wrap">
    <template v-if="!isEmpty">
      <div class="list-item" v-for="(item, prop) in list" :key="prop">
        <div class="card w-75">
          <ListItem @del="deleteItem" :obj="item" />
        </div>
      </div>
    </template>

    <div v-else class="alert alert-primary" role="alert">List is empty</div>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";
export default {
  name: "BudgetList",
  components: {
    ListItem,
  },
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  data: () => ({
    header: "Budget List",
    emptyTitle: "Empty List",
  }),
  computed: {
    isEmpty() {
      return !Object.keys(this.list).length;
    },
  },
  methods: {
    deleteItem(id) {
      this.$emit("deleteItem", id);
    },
  },
};
</script>

<style scoped>
.budget-list-wrap {
  max-width: 800px;

  margin-left: auto;
  margin-right: auto;

  background-color: rgb(226, 220, 220);
}

.list-item {
  padding: 0px 2px;
  margin-left: 158px;
}
</style>
