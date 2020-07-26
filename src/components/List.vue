<template>
  <div class="container">
    <section class="toolbar z-depth-2">
      <Toolbar v-on:add-item="addItem" v-bind:GPA="GPA" />
    </section>

    <section class="grey darken-4">
      <div v-bind:key="course.id" v-for="course in courses">
        <ListItem
          v-bind:course="course"
          v-on:remove-item="removeItem"
          v-on:register-score="updateGPA"
        />
      </div>
    </section>
  </div>
</template>

<script>
import Toolbar from "./ListToolbar.vue";
import ListItem from "./ListItem.vue";

export default {
  name: "List",
  components: {
    Toolbar,
    ListItem,
  },
  props: ["courses"],
  data() {
    return {
      GPA: null,
      sumOfProducts: 0,
      totalCredits: 0,
    };
  },
  methods: {
    addItem(newItem) {
      this.$emit("add-item", newItem);
    },
    removeItem() {
      this.$emit("remove-item");
    },
    updateGPA(ratio, credits) {
      this.sumOfProducts += ratio * credits;
      this.totalCredits += credits;
      this.GPA = (this.sumOfProducts / this.totalCredits).toFixed(2);
    },
  },
};
</script>

<style scoped>
</style>