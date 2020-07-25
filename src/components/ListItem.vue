<template>
  <label>
    <input type="checkbox" v-on:change="markSelected" />
    <span class="white-text">[{{course.id}}] {{course.title}}</span>
  </label>
</template>

<script>
export default {
  name: "ListItem",
  props: ["course"],
  methods: {
    markSelected() {
      this.course.selected = !this.course.selected;
    },
  },
};
</script>

<style scoped>
</style>