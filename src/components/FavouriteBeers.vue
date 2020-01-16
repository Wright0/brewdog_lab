<template lang="html">
  <div v-if='favouriteBeers.length'>
    <h1>Our favourite beers</h1>
    <article v-for="beer in favouriteBeers">
      <h3>{{beer.name}}</h3>
      <h4>{{beer.tagline}}</h4>
      <dl>
        <dt>Alcohol content:</dt>
        <dd>{{beer.abv}}%</dd>
      </dl>
      <img class="beer-image-fav" :src="beer.image_url" alt="image of beer selected">
      <button type="button" @click="removeBeerFromFavourites(beer.id)">Unfavourite me</button>
    </article>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'favourite-beers',
  props: ['favouriteBeers'],
  methods: {
    removeBeerFromFavourites(id){
      eventBus.$emit('delete-beer-from-favourite', id)
    }
  }
}
</script>

<style lang="css" scoped>

.beer-image-fav {
  height: 100px;
}
</style>
