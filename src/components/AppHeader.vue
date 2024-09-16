<script>
export default {
  data() {
    return { 
      
    }
  },
  methods: {
    search() {
      console.log('stai cercando')

    }
  }
}
</script>

<template>
  <header class="bg-black">
    <div class="container d-flex justify-content-between align-items-center py-2">
      <h1 class="text-danger text-uppercase">
        bootflix
      </h1>

      <form @submit.prevent="search()" class="d-flex">
        
        <input type="text" class="my-2" placeholder="Seacrh">
  
        <button class="text-uppercase btn btn-warning my-2">
          search
        </button>
      </form>

    </div>
  </header>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables' as *;
</style>
