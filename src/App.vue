<template>
  <div id="app">
    <Header id="header" />
    <List id="body" v-bind:courses="courses" />
    <Footer id="footer" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import List from "./components/List.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    Footer,
    List,
  },
  data() {
    return {
      courses: [
        {
          id: "ET2015",
          title: "Electronics",
          credits: 4,
          selected: false,
        },
        {
          id: "MI1012",
          title: "Math I",
          credits: 3,
          selected: false,
        },
        {
          id: "MI1042",
          title: "Math IV",
          credits: 3,
          selected: false,
        },
      ],
    };
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
  height: 100%;
}

body {
  font-family: "Tahoma", "Geneva", sans-serif;
  line-height: 1.2;
  background: #1a1a1a;
  color: #e7e7e7;
  min-height: 100%;
}

#app {
  height: 100vh;
}

#header {
  height: 10vh;
}

#body {
  height: 75vh;
}

#footer {
  height: 5vh;
}

.checkbox {
  margin-right: 5px;
  border-radius: 2px;
}

.btn {
  margin: 0 5px;
  padding: 5px;
  outline: none;
  background: rgba(0, 0, 0, 0.4);
  border: none;
  border-radius: 5px;
  color: #e7e7e7;
  font-family: "Tahoma", "Geneva", sans-serif;
  font-size: 1em;
}
.btn:hover {
  background: rgba(0, 0, 0, 0.6);
}
</style>
