<template>
  <div id="app">
    <selected-beer :beers='beers'></selected-beer>
  </div>
</template>

<script>
import SelectBeer from './components/SelectBeer.vue'

export default {
  name: 'app',
  data(){
    return {
      beers:[],
      selectedBeerId: 0,
      favouriteBeers: []
    };
  },
  // computed: {
  //   selectedBeerObj(){
  //
  //   }
  // }
  components: {
    "selected-beer": SelectBeer
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
      .then(response => response.json())
      .then(beerArray => this.beers = beerArray)
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
