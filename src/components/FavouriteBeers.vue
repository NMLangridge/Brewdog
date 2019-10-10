<template lang="html">
  <div id="fav" v-if='beers'>
    <h2>Favourites</h2>
    <ul>
      <li v-for='favourite in beers'>{{favourite.name}}</li>
    </ul>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'favourite-beers',
  props: ['beers']
}
</script>

<style lang="css" scoped>
#fav {
  position: absolute;
  right: 50%;
  top: 55px;
}
</style>
