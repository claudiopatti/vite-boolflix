<script>
import { store } from '../store.js';
import SingleCardFilm from './SingleCardFilm.vue';
import SingleCardSerieTv from './SingleCardSerieTv.vue';


export default {
  data() {
    return { 
      store:store,

    }
  },
  components: {
    SingleCardFilm,
    SingleCardSerieTv
  },

}
</script>

<template>
  <main class="bg-primary">
    <div class="container">
      <div class="row">
        <div v-for="(cardFiml, index) in store.cardsFimls" :key="index" class="col-12 col-sm-6 col-md-3">
          <SingleCardFilm :card = "cardFiml" :vote = "cardFiml.vote_average" />
        </div>
      </div>

      <div class="row">
        <div v-for="(cardSerie, index) in store.cardsSerieTv" :key="index" class="col-12 col-sm-6 col-md-3">
          <SingleCardSerieTv :cardSeries = "cardSerie" :vote = "cardSerie.vote_average" />
        </div>
      </div>

    </div>

  </main>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables' as *;
</style>
