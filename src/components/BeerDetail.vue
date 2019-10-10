<template lang="html">
  <div v-if='beer'>
    <h2>{{beer.name}}</h2>

    <div id="fav">
      <button v-on:click="handleClick">Favourite</button>
    </div>

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
import {eventBus} from '../main.js'

export default {
  name: 'beer-detail',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('favourite-beers', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
