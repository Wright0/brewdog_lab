<template lang="html">
  <select v-model='selectedBeerId' @change='handleSelected'>
    <option v-for='beer in beers' :value='beer.id'>{{beer.name}}</option>
  </select>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'selected-beer',
  data(){
    return{
      selectedBeerId: 0
    }
  },
  props: ['beers'],
  methods: {
    handleSelected(){
      eventBus.$emit('selected-beer', this.selectedBeerId);
    }
  }
}
</script>

<style lang="css" scoped>

</style>
