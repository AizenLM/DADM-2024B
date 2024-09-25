<script setup>
import { ref } from 'vue'
// Modelo
const header = ref('App lista de compras')
const itemsList2 = ref([
  {
    'id': 101,
    'name': '10 bolillos',
  },

  {
    'id': 102,
    'name': '1 lata volt',
  },
  {
    'id': 103,
    'name': '1 bote de cafe',
  },

  {
    'id': 104,
    'name': 'chetos flaming hot',
  }
])
</script>

<template>
  <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>
  <ul>
    <li v-for="({id, name}, i) in itemsList2" :key="id">{{i + 1}} {{name}}</li>
  </ul>
</template>
<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>
