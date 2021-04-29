<template>
  <div id="app">
    <h1>{{showLabels}}</h1>
    <Button @toggleSelect="toggleText"></Button>
    <ThreeApp :showDerivations="showLabels"/>
  </div>
</template>

<script>
import ThreeApp from './components/ThreeApp.vue'
import Button from './components/Button.vue'

export default {
  name: 'App',
  components: {
    ThreeApp,
    Button
  },
  data() {
    return {
      showLabels: false,
    }
  },
  methods: {
    toggleText: function(){
      this.showLabels = !this.showLabels
    }
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
