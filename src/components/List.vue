<template>
  <div class="container">
    <section class="options">
      <Toolbar v-on:add-item="addItem" v-on:remove-item="removeItem" />
    </section>

    <section class="content">
      <div class="list-item" v-bind:key="course.id" v-for="course in courses">
        <ListItem v-bind:course="course" />
      </div>
    </section>

    <section class="result">
      <input
        class="btn waves-effect waves-light white-text"
        type="button"
        value="Calculate your GPA"
      />
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
  methods: {
    addItem(newItem) {
      this.$emit("add-item", newItem);
    },
    removeItem() {
      this.$emit("remove-item");
    },
  },
};
</script>

<style scoped>
</style>