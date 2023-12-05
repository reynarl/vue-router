<script setup>
import { RouterLink } from 'vue-router';
defineProps({
  name: String,
  url : String
})


</script>

<template>
  <div class="card">
    <h2 class="card-title"> </h2>
    <div class="card-body">
      <router-link :to="`/pokemons/${name}`">
        <p>{{ name }}</p>
      </router-link>
    </div>
  </div>
</template>