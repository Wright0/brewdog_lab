<template lang="html">
  <div v-if='favouriteBeers.length'>
    <h1>Our favourite beers</h1>
    <div class="favourite-beers">
      <article v-for="beer in favouriteBeers">
        <h3>{{beer.name}}</h3>
        <h4>{{beer.tagline}}</h4>
        <dl>
          <dt>Alcohol content:</dt>
          <dd>{{beer.abv}}%</dd>
        </dl>
        <img class="beer-image-fav" :src="beer.image_url" alt="image of beer selected">
        <button type="button" class="delete-me-button" @click="removeBeerFromFavourites(beer.id)">Unfavourite me</button>
      </article>
    </div>
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

  article {
    display: flex;
    flex-direction: column;
    justify-content: center;
    box-sizing: border-box;
    align-items: center;

    padding: 10px;
    margin: 10px;
    max-width: 350px;

    background-color: white;
    border-radius: 5px;
  }

  h3, h4 {
    margin: 5px;
  }

  dd {
    margin: 0px;
  }


  .favourite-beers {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    color: black;
  }

  .beer-image-fav {
    width: 80px;
    display: block;
  }

  .delete-me-button {
    width: 100px;
  }
</style>
