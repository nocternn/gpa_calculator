<template>
  <form class="col s12 grey darken-4 white-text">
    <div class="row input-field col s8 valign-wrapper">
      <div class="input-field col s8">
        <input id="course" class="white-text" type="text" name="course" v-model="course" />
        <label for="course">Course title</label>
      </div>

      <div class="input-field col s4">
        <input
          class="btn waves-effect waves-light white-text"
          type="button"
          value="Add"
          v-on:click="addItem"
        />
      </div>
    </div>

    <h3>Your GPA: {{GPA}}</h3>
  </form>
</template>

<script>
export default {
  name: "Toolbar",
  props: ["GPA"],
  data() {
    return {
      course: "",
    };
  },
  methods: {
    addItem() {
      const newItem = {
        id: this.course,
        title: this.course,
        selected: false,
      };

      this.$emit("add-item", newItem);
    },
  },
};
</script>

<style scoped>
form {
  margin: 5vh 0;
  padding: 2vh;
}

#calculateGPA {
  margin-right: 5vh;
}
</style>