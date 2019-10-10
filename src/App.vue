<template lang="html">
  <div>
    <h1>Brewdog</h1>
    <h2>Beer Menu</h2>
    <beers-list :beers='beers'></beers-list>
    <beer-detail :beer='selectedBeer'></beer-detail>
    <favourite-beers :beers='favouriteBeers'></favourite-beers>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import BeersList from './components/BeersList.vue';
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeers from './components/FavouriteBeers.vue';

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(result => result.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })

    eventBus.$on('favourite-beers', (beer) => {
      this.favouriteBeers.push(beer);
    })

  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  }
}
</script>

<style lang="css" scoped>
</style>
