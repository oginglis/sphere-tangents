<template>
  <div class="wrap" v-on:click="select">
    <button class="button" >{{ showDerivations ?  'Hide Derivations' : 'Show Derivations' }}</button>
  </div>
</template>

<script>


export default {
  title: 'Sphere Tangents',
  name: 'Button',
  props: {
    showDerivations: Boolean,
  },
  methods: {
    select: function(){
      this.$emit('toggleSelect')
    },
  },

  data() {
    return {
    }
  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  position: relative;
  border-radius: 100;


}

.wrap {
position: fixed;
top:10 !important;
left: 10 !important;
display: inline-block;


}
</style>
