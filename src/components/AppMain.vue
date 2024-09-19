<script>
// store globale da dove salviamo e prendiamo dati
import { store } from '../store.js';
// componente per creare singola card di film e serie tv
import singleCardFilmSerie from './singleCardFilmSerie.vue';


export default {
  data() {
    return { 
      store:store,

    }
  },
  components: {
    singleCardFilmSerie
  },

}
</script>

<template>
  <main class="bg-secondary ">
    <div class="container">
      <h2 class="py-5">
        FILM
      </h2>
      <div class="row">
        <!-- ciclo per creare le card dei film  -->
        <div v-for="(cardFiml, index) in store.cardsFimls" :key="index" class="col-12 col-sm-6 col-md-4 col-lg-3 pb-5">
          <!-- componente per creare singola card  -->
          <singleCardFilmSerie 
            :title="cardFiml.title" 
            :originalTitle="cardFiml.original_title" 
            :language="cardFiml.original_language" 
            :vote = "cardFiml.vote_average" 
            :overview= "cardFiml.overview"
            :posterPath="cardFiml.poster_path" /> 
        </div>
      </div>

      <h2 class="my-5">
        SERIE
      </h2>
      <div class="row">
        <!-- ciclo per creare le card delle serie  -->
        <div v-for="(cardSerie, index) in store.cardsSerieTv" :key="index" class="col-12 col-sm-6 col-md-4 col-lg-3 pb-5">
          <!-- componente per creare singola card  -->
          <singleCardFilmSerie 
            :title="cardSerie.name" 
            :originalTitle="cardSerie.original_name" 
            :language="cardSerie.original_language" 
            :vote = "cardSerie.vote_average" 
            :overview= "cardSerie.overview"
            :posterPath="cardSerie.poster_path" />
        </div>
      </div>

    </div>

  </main>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables' as *;
main {
  min-height: calc(100vh - 72px);
}

</style>
