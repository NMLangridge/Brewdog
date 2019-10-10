<template lang="html">
  <div v-if='beer'>
    <h2>{{beer.name}}</h2>
    <p>Name: {{beer.name}}</p>
    <p>Tagline: {{beer.tagline}}</p>
    <p>First Brewed: {{beer.first_brewed}}</p>
    <p>Description: {{beer.description}}</p>
    <p>Alcohol Level: {{beer.abv}}%</p>
    <p>Food Pairing: </p>
    <ul v-for="food_pairing in beer.food_pairing">
      <li>{{food_pairing}}</li>
    </ul>
    <img :src="beer.image_url" :alt="beer.name">
  </div>
</template>

<script>
export default {
  name: 'beer-detail',
  props: ['beer']
}
</script>

<style lang="css" scoped>
</style>
