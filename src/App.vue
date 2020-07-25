<template>
  <div id="app">
    <Header id="header" />
    <List
      id="body"
      v-bind:courses="courses"
      v-on:add-item="addItem"
      v-on:remove-item="removeItems"
    />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import List from "./components/List.vue";

export default {
  name: "App",
  components: {
    Header,
    List,
  },
  data() {
    return {
      courses: [],
    };
  },
  methods: {
    addItem(newItem) {
      this.courses = [...this.courses, newItem];
    },
    removeItems() {
      this.courses = this.courses.filter((todo) => todo.selected !== true);
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  overflow-y: scroll;
}

body {
  font-family: "Arial", "Tahoma", sans-serif;
  line-height: 1.4;
}

#header {
  height: 10vh;
}
</style>
