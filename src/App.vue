<template>
  <div id="app">
    <selected-beer></selected-beer>
  </div>
</template>

<script>
import SelectBeer from './components/SelectBeer.vue'

export default {
  name: 'app',
  components: {
    "selected-beer": SelectBeer
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
