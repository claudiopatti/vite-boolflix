<script>
import { store } from '../store.js';
import onlySingleCardFilm from './onlySingleCardFilm.vue';
import onlySingleCardSerieTv from './onlySingleCardSerieTv.vue';


export default {
  data() {
    return { 
      store:store,

    }
  },
  components: {
    onlySingleCardFilm,
    onlySingleCardSerieTv
  },

}
</script>

<template>
  <main class="bg-primary">
    <div class="container">
      <div class="row">
        <div v-for="(cardFiml, index) in store.cardsFimls" :key="index" class="col-12 col-sm-6 col-md-3">
          <onlySingleCardFilm :card = "cardFiml"  :languageFilm="cardFiml.original_language"/>
        </div>
      </div>

      <div class="row">
        <div v-for="(cardSerie, index) in store.cardsSerieTv" :key="index" class="col-12 col-sm-6 col-md-3">
          <onlySingleCardSerieTv :cardSeries = "cardSerie"  />
        </div>
      </div>

    </div>

  </main>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables' as *;
</style>
