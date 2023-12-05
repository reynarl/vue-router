<script setup>
import { useRouter } from 'vue-router'; 

const router = useRouter
const backHome = () => {
  router.push('/pokemons')
}

</script>

<template>
  <h1>PAGINA 404</h1>
  <button @click="backHome">INICIO</button>
</template>