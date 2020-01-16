<template lang="html">
  <select name="">
    <option v-for='beer in beers' :value='beer.id'>{{beer.name}}</option>
  </select>
<!-- <p v-if='beers'>hello {{beers[2].name}}</p> -->
</template>
x
<script>
export default {
  name: 'selected-beer',
  data(){
    return{
      selectedBeerId: 0
    }
  },
  props: ['beers']
}
</script>

<style lang="css" scoped>
</style>
