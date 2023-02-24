<template>
  <div id="app">
    <dasboard/>
    <router-view />
  </div>
</template>

<script>
import Dasboard from './views/Dasboard.vue';
export default {
  name: "App",
  components: {
    Dasboard
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
  margin-top: 60px;
}
</style>
