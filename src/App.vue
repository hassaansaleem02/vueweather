<template>
  <Head />
  <weather />
</template>

<script>
import Head from "./components/header.vue";
import weather from "./components/weather.vue";

export default {
  name: "App",
  components: {
    Head,
    weather,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0%;
  padding: 0%;
  background: url("./assets/back3 (2).jpg") no-repeat center center fixed;
  background-size: cover;
  
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
