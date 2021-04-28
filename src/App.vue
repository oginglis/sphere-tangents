<template>
  <div id="app">
    <ThreeApp msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import ThreeApp from './components/ThreeApp.vue'

export default {
  name: 'App',
  components: {
    ThreeApp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0 0 0 0;
}
</style>
