<template>
  <div id="app">
    <heat-map></heat-map>
  </div>
</template>

<script>
import HeatMap from './components/HeatMap.vue';

export default {
  name: 'App',
  components: {
    HeatMap,
  },
};
</script>

<style>
body {
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 100vw;
  height: 100vh;
}
</style>
