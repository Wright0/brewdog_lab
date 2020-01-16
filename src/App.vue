<template>
  <div id="app">
    <h1>Hair of the Brewdog</h1>
    <selected-beer :beers='beers'></selected-beer>
    <display-beer :beerObject='selectedBeerObj'></display-beer>
    <favourite-beers :favouriteBeers='favouriteBeers'></favourite-beers>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import SelectBeer from './components/SelectBeer.vue'
import DisplayBeer from './components/DisplayBeer.vue'
import FavouriteBeers from './components/FavouriteBeers.vue'

export default {
  name: 'app',
  data(){
    return {
      beers:[],
      selectedBeerId: 0,
      favouriteBeers: []
    };
  },
  computed: {
    selectedBeerObj(){
      return this.beers.find(beer => beer.id === this.selectedBeerId)
    }
  },
  components: {
    "selected-beer": SelectBeer,
    "display-beer": DisplayBeer,
    "favourite-beers": FavouriteBeers
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
      .then(response => response.json())
      .then(beerArray => this.beers = beerArray)

    eventBus.$on('selected-beer', beerId => this.selectedBeerId = beerId)
    eventBus.$on('send-favourite-beer', beerObj => this.favouriteBeers.push(beerObj))
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
