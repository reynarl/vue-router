<script setup>
import { ref } from 'vue'

const count = ref(0)

const handleClickAdd = () => {
  count.value ++
}

const handleClickMinus = () => {
  count.value --
}


</script>

<template>
<div class="containter">
  <div>
    <h2>Contador</h2>
    <h2>{{ count }}</h2>
    <button class="btn btn-primary me-1" @click="handleClickMinus" :disabled="count <= 0">-</button>
    <button class="btn btn-primary" @click="handleClickAdd">+</button>
    <button class="btn btn-danger ms-2" @click="() => count = 0">Reset</button>
  </div>
</div>
</template>
