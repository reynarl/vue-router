<script setup>
import { ref } from 'vue';
import axios from 'axios';
import { useRoute, useRouter } from 'vue-router';


const pokemon = ref({})
const loading = ref(false)

const route = useRoute()
const router = useRouter()

const getData = async() => {
  try {
    loading.value = true
    const {data} = await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
    pokemon.value = data
    loading.value = false
  } catch (error) {
    console.log(error);
    loading.value = false
  }
}
getData()

const back = () => {
  router.push('/pokemons')
}
</script>

<template>
  <button class="btn btn-outline-success" @click="back">Regresar</button>
  <div v-if="!loading">
    <!-- Acceder al name que viene en la ruta -->
    <h1>Pokemon: {{ $route.params.name }}</h1>
    <img :src="pokemon?.sprites?.back_default" alt="">
    <!-- <p>{{ pokemon.sprites.back_default ? pokemon.sprites.back_default : 'cargando..' }}</p> -->
  </div>
</template>