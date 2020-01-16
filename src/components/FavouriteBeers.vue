<template lang="html">
  <div>
    <h2>Favourite Beers</h2>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'favourite-beers',
  props: ['favouriteBeers']
}
</script>

<style lang="css" scoped>
</style>
