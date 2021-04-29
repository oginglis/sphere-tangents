<template>
  <div id="app">
    <Button :showDerivations="showLabels" @toggleSelect="toggleText"></Button>
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
    },
    toggleBodyClass(addRemoveClass, className) {
      const el = document.body;

      if (addRemoveClass === 'addClass') {
        el.classList.add(className);
      } else {
        el.classList.remove(className);
      }
    },
  },

  mounted() {
    this.toggleBodyClass('addClass', 'bodywork');
  },
  destroyed() {
    this.toggleBodyClass('removeClass', 'bodywork');
  }
}
</script>

<style >
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0 0 0 0;
},

.bodywork {
  margin: 0 ;
  padding: 0;

}
</style>
