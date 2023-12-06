<script setup>
import { ref } from 'vue';
import axios from 'axios';
import { useRoute, useRouter } from 'vue-router';


const pokemon = ref({})
const loading = ref(false)
const message = ref(null)

const route = useRoute()
const router = useRouter()

const getData = async() => {
  loading.value = true

  try {
    const {data} = await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
      pokemon.value = data
  } catch (error) {
      message.value = 'No se pudieron cargar los datos del servidor'
  } finally{
    loading.value = false
  }
}
getData()

const back = () => {
  router.push('/pokemons')
}
</script>

<template>
  <div>
    <button class="btn btn-outline-success" @click="back">Regresar</button>
    
  <div>
    <!-- Acceder al name que viene en la ruta -->
    <h1>Pokemon: {{ $route.params.name }}</h1>
    <img :src="pokemon?.sprites?.back_default" alt="">
    <p v-if="message" class="alert alert-danger mt-3">{{ message }}</p>
  </div>
  </div>
</template>