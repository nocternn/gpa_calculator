<template>
  <div>
    <input type="checkbox" class="checkbox" />
    <span>[{{course.id}}] {{course.title}}</span>
  </div>
</template>

<script>
export default {
  name: "ListItem",
  props: ["course"],
};
</script>

<style scoped>
div {
  padding: 10px;
}
</style>