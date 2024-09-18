<script>
import axios from 'axios';

import { store } from './store.js';

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';


export default {
  data() {
    return { 
      store: store,
      // la mia ky delle api per entrare nel database dell'api in questione
      apiKey: 'f4209377e7b8796244aae146220bb25c', 
      
      
    }
  },
  components: {
    AppHeader,
    AppMain
  },
  methods: {
    performSearchFilm() {
      //importazione APi per recuperare film
      axios
      .get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: this.apiKey,
          query: this.store.FilmSerieSearch
        }
      })  
      .then((res) => {
  
        this.store.cardsFimls = res.data.results
      })

      //controllo in caso di errori e risolvo con pulizia dell'array originaria
      .catch((err) => {
        this.store.cardsFilms = []
      });

      //importazione APi per recuperare serie

        axios
      .get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: this.apiKey,
          query: this.store.FilmSerieSearch
        }
      })
      .then((res) => {
  
        this.store.cardsSerieTv = res.data.results
      })

      //controllo in caso di errori e risolvo con pulizia dell'array originaria
      .catch((err) => {
        this.store.cardsSerieTv = []
      })
    },
  },
  
  created() {
    //richiamo della funzione della chiamata all'api dopo in caricamento della pagina
    this.performSearchFilm()
  }
}
</script>

<template>
  <div>
    <AppHeader @search="performSearchFilm() " />

    <AppMain />
    
  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
// Import all of Bootstrap's CSS
@import "bootstrap/scss/bootstrap";
</style>
