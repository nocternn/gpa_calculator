<template>
  <div class="card grey darken-4 white-text">
    <div id="main" class="z-depth-2">
      <div class="card-content">
        <span class="card-title">{{course.title}}</span>
        <div class="row">
          <p class="col s6">Final score: {{finalScore10}} - {{finalScore4}}</p>
          <p class="col s6">Credits: {{credits}}</p>
        </div>
      </div>
      <div class="card-action row">
        <div id="action-toggle-extra" class="input-field col s6">
          <input
            id="toggle-extra"
            class="white-text"
            type="button"
            value="Expand"
            v-on:click="toggleExtra"
          />
        </div>
        <div id="action-remove" class="input-field col s6">
          <input class="white-text" type="button" value="Remove" v-on:click="removeItem" />
        </div>
      </div>
    </div>

    <div id="extra" v-bind:class="{hide: this.hideExtra }">
      <div class="row">
        <div class="input-field col s6">
          <input id="midterm" type="number" class="white-text" v-model="midterm" />
          <label for="midterm">Midterm examitation score</label>
        </div>
        <div class="input-field col s6">
          <input id="finals" type="number" class="white-text" v-model="finals" />
          <label for="finals">Final examination score</label>
        </div>
      </div>

      <div class="row">
        <div class="input-field col s6">
          <input id="midterm-ratio" type="number" class="white-text" v-model="midtermRatio" />
          <label for="midterm-ratio">Midterm score ratio</label>
        </div>
        <div class="input-field col s6">
          <input id="credits" type="number" class="white-text" v-model="credits" />
          <label for="credits">Course credits</label>
        </div>
      </div>

      <div class="row">
        <input
          class="btn waves-effect waves-light white-text"
          type="button"
          value="Calculate final grade"
          v-on:click="calculate"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ListItem",
  props: ["course"],
  data() {
    return {
      hideExtra: true,
      midterm: null,
      finals: null,
      midtermRatio: null,
      credits: null,
      finalScore10: null,
      finalScore4: null,
      finalRatio: null,
    };
  },
  methods: {
    toggleExtra() {
      this.hideExtra = !this.hideExtra;
    },
    removeItem() {
      this.course.selected = !this.course.selected;
      this.$emit("remove-item");
    },
    calculate() {
      this.finalScore10 =
        this.midtermRatio * this.midterm +
        (1 - this.midtermRatio) * this.finals;

      if (this.finalScore10 < 4.0) {
        this.finalScore4 = "F";
        this.finalRatio = 0;
      } else if (this.finalScore10 < 5.0) {
        this.finalScore4 = "D";
        this.finalRatio = 1;
      } else if (this.finalScore10 < 5.5) {
        this.finalScore4 = "D+";
        this.finalRatio = 1.5;
      } else if (this.finalScore10 < 6.5) {
        this.finalScore4 = "C";
        this.finalRatio = 2;
      } else if (this.finalScore10 < 7) {
        this.finalScore4 = "C+";
        this.finalRatio = 2.5;
      } else if (this.finalScore10 < 8) {
        this.finalScore4 = "B";
        this.finalRatio = 3;
      } else if (this.finalScore10 < 8.5) {
        this.finalScore4 = "B+";
        this.finalRatio = 3.5;
      } else if (this.finalScore10 < 9.5) {
        this.finalScore4 = "A";
        this.finalRatio = 4;
      } else {
        this.finalScore4 = "A+";
        this.finalRatio = 4;
      }

      this.$emit("register-score", this.ratio * Number(this.credits));
    },
  },
};
</script>

<style scoped>
* {
  margin: 0;
}

.card-action input {
  border: none;
  background: none;
  outline: none;
}

#extra {
  padding: 2vh;
}
#extra .row {
  margin: 2vh 0;
}
</style>