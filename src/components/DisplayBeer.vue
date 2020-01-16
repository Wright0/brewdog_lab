<template lang="html">
  <div>

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
    </div>

  </div>
</template>

<script>
export default {
  name: 'display-beer',
  props: ['beerObject']
}
</script>

<style lang="css" scoped>

.beer-image {
  height: 250px;
}
</style>
