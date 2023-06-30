<template>
  <div v-bind:style="{ color: color }" class="total-value">
    Balance: {{ total }}
  </div>
</template>

<script>
export default {
  name: "TotalBalance",
  data: () => ({
    total: 0,
    color: "black",
  }),
  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },
  watch: {
    list(e) {
      console.log(e);
      let tota = 0;
      if (Object.entries(this.list).length == 0) this.total = 0;
      else {
        for (let el in e) {
          if (e[el].type == "INCOME") tota += e[el].value;
          else if (e[el].type == "OUTCOME") tota -= e[el].value;
          this.total = tota;
        }
      }
    },
    total(e) {
      if (e > 0) this.color = "green";
      else if (e < 0) this.color = "red";
      else this.color = "black";
    },
  },
};
</script>

<style scoped>
.total-value {
  font-size: 26px;
  text-transform: uppercase;
  padding: 20px;
  text-align: center;
}
.total-value {
  max-width: 300px;
  margin-left: auto;
  margin-right: auto;
}
</style>
