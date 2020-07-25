<template>
  <div class="container">
    <div class="options">
      <input type="checkbox" class="checkbox" />
      <input type="button" value="Add" class="btn" />
      <input type="button" value="Remove" class="btn" />
    </div>

    <div class="content">
      <div class="list-item" v-bind:key="course.id" v-for="course in courses">
        <ListItem v-bind:course="course" />
      </div>
    </div>

    <div class="result">
      <input type="button" value="Calculate your GPA" class="btn" />
    </div>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";

export default {
  name: "List",
  components: {
    ListItem,
  },
  props: ["courses"],
};
</script>

<style scoped>
.container {
  width: 80%;
  margin: 5vh auto;
  border: 2px solid #0c0c0c;
  border-radius: 5px;
}

.options {
  height: 10%;
  padding: 1vh;
  border-bottom: 2px solid #0c0c0c;
}

.content {
  height: 80%;
}
.content .list-item {
  padding: 1vh 0;
  border-bottom: 1px solid #0c0c0c;
}

.result {
  height: 10%;
  padding: 1vh;
  border-top: 2px solid #0c0c0c;
}
</style>