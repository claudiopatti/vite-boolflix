<script>
import axios from 'axios';

/* 
  Per importare ed utilizzare un componente dentro un altro devo SEMPRE seguire questi 3 passi:
  1) Importazione del componente
  2) Dichiarazione del componente
  3) Utilizzo del componente
*/
// 1) Importazione del componente
import { store } from './store.js';

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';


export default {
  data() {
    return { 
      store: store
      
    }
  },
  // 2) Dichiarazione del componente
  components: {
    AppHeader,
    AppMain
  },
  methods: {
    performSearch() {
      axios
      .get('https://api.themoviedb.org/3/search/movie?api_key=f4209377e7b8796244aae146220bb25c&query=' + this.store.filmSearch)
        .then((res) => {
          console.log(res.data.results)
    
          this.store.cardsFimls = res.data.results
        })
        .catch((err) => {
          this.store.cardsFilms = []
        })

    }
  },
  
  created() {
    this.performSearch()
  }
}
</script>

<template>
  <div>
    <!-- 3) Utilizzo del componente -->
    <AppHeader @search="performSearch()" />

    <AppMain />
    
  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
// Import all of Bootstrap's CSS
@import "bootstrap/scss/bootstrap";
</style>
