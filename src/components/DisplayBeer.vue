<template lang="html">
  <div class="beer-object" v-if="beerObject">
    <article>
      <h3>{{beerObject.name}}</h3>
      <h4>{{beerObject.tagline}}</h4>
      <dl>
        <dt>Description:</dt>
        <dd>{{beerObject.description}}</dd>

        <dt>Alcohol content:</dt>
        <dd>{{beerObject.abv}}%</dd>
      </dl>
    </article>

    <div>
      <img class="beer-image" :src="beerObject.image_url" alt="image of beer selected">
      <button @click="saveFavouriteBeer">Favourite This Beer</button>
    </div>

  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'display-beer',
  props: ['beerObject'],
  methods: {
    saveFavouriteBeer(){
      eventBus.$emit('send-favourite-beer', this.beerObject);
    }
  }
}
</script>

<style lang="css" scoped>

  button {
    cursor: pointer;
    border: 1px solid white;
    border-radius: 5px;
    min-width: 100px;
    margin: 20px;
    background-color: #022F40;
    color: white;
    font-size: 14px;
  }

  button:hover{
    color: #022F40;
    background-color: white;
  }

  button:focus {
    outline: 0;
  }

  dt {
    font-weight: bold;
  }
  dd {
    margin: 5px;
  }

  .beer-object {
    display: flex;
    flex-direction: row;
    box-sizing: border-box;
    align-items: center;
    margin: 0 auto;
    max-width: 600px;
  }

  .beer-image {
    margin: 20px;
    height: 250px;
  }
</style>
