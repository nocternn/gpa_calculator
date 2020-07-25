<template>
  <form class="col s12 valign-wrapper">
    <div class="row input-field col s8 valign-wrapper">
      <div class="input-field col s8">
        <input id="course" class="white-text" type="text" name="course" v-model="course" />
        <label for="course">Course ID</label>
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

    <div class="input-field col s4">
      <input
        class="btn waves-effect waves-light white-text"
        type="button"
        value="Remove"
        v-on:click="removeItem"
      />
    </div>
  </form>
</template>

<script>
export default {
  name: "Toolbar",
  data() {
    return {
      course: "",
    };
  },
  methods: {
    addItem() {
      const newItem = {
        id: this.course,
        title: "New Item",
        credits: 4,
        selected: false,
      };

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