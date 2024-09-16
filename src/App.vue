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
      store: store,
      
      
    }
  },
  // 2) Dichiarazione del componente
  components: {
    AppHeader,
    AppMain
  },
  methods: {
    performSearchFilm() {
      axios
      .get('https://api.themoviedb.org/3/search/movie?api_key=f4209377e7b8796244aae146220bb25c&query=' + this.store.filmSearch )
        .then((res) => {
          // console.log(res.data.results)
          // if (res.data.results.original_language  ) {
            
          // }
    
          this.store.cardsFimls = res.data.results
        })
        .catch((err) => {
          this.store.cardsFilms = []
        })

      // axios
      // .get('https://api.themoviedb.org/3/search/tv?api_key=f4209377e7b8796244aae146220bb25c&query=' + this.store.filmSearch )
      //   .then((res) => {
      //     console.log(res.data.results)
    
      //     this.store.cardsSerieTv = res.data.results
      //   })
      //   .catch((err) => {
      //     this.store.cardsSerieTv = []
      //   })

    },
    performSearchSeries() {
      axios
      .get('https://api.themoviedb.org/3/search/tv?api_key=f4209377e7b8796244aae146220bb25c&query=' + this.store.filmSearch )
        .then((res) => {
          console.log(res.data.results)
    
          this.store.cardsSerieTv = res.data.results
        })
        .catch((err) => {
          this.store.cardsSerieTv = []
        })
    }
  },
  
  created() {
    this.performSearchFilm(),
    this.performSearchSeries()


  }
}
</script>

<template>
  <div>
    <!-- 3) Utilizzo del componente -->
    <AppHeader @search="performSearchFilm(), performSearchSeries() " />

    <AppMain />
    
  </div>
</template>

<style lang="scss">
@use 'assets/scss/main' as *;
// Import all of Bootstrap's CSS
@import "bootstrap/scss/bootstrap";
</style>
