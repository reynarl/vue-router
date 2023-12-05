<script setup>

import axios from 'axios'
import { ref } from 'vue';

import PokemonCard from '../components/pokemonCard.vue'

const pokemons = ref([])

const getData = async () => {
  try {
    const { data } = await axios.get('https://pokeapi.co/api/v2/pokemon')
    pokemons.value = data.results
    console.log(data.results);
  } catch (error) {
    pokemons.value = []
    console.log(error);
  }
}

getData()

</script>

<template>
  <h1>Pokemons</h1>
  <PokemonCard 
    v-for="pokemon in pokemons"
    class="mt-2"
    :key="pokemon.name"
    :name="pokemon.name"
  />
</template>