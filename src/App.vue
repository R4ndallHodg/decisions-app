<template>
  <Indecision />
</template>

<script>
import Indecision from "./components/Indecision.vue";

export default {
  name: "App",
  components: {
    Indecision,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column-reverse;
  justify-content: flex-start;
  width: 100%;
  height: 100%;
  min-height: 100vh;
  max-width: 100vh;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
