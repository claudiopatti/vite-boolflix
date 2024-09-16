<script>
import { store } from '../store.js';
import onlySingleCardFilm from './onlySingleCardFilm.vue'

export default {
  data() {
    return { 
      store:store,

    }
  },
  components: {
    onlySingleCardFilm
  },

}
</script>

<template>
  <main class="bg-primary">
    <div class="container">
      <div class="row">
        <div v-for="(card, index) in store.cardsFimls" :key="index" class="col-12 col-sm-6 col-md-3">
          <onlySingleCardFilm :card = "card"/>
        </div>
      </div>

    </div>

  </main>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables' as *;
</style>
