<script setup>
import { ref } from 'vue'
// Modelo
const header = ref('App lista de compras')
const newItem = ref('Nuevo Item')
const newItemPriority = ref('low');
const itemsList2 = ref([
  {
    'id': 101,
    'name': '10 botextlillos',
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
 {{ console.log(newItem)}}
 {{ console.log(newItemPriority) }}
  <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>
  <input v-model.lazy="newItem" type="text" placeholder="Agregar articulo"> {{ newItem=='Mexico'?'ola':'a'  }} 
  <!-- Radio buttons---->
  <label for="">
    <input type="radio" value="high" v-model="newItemPriority">Alto
    </label>
    <label for="">
      <input type="radio" value="low" v-model="newItemPriority">Bajo
      {{ newItemPriority == "high" ? "🔥":"🧊" }}
      </label>

  <ul>
    <li v-for="({id, name}, i) in itemsList2" :key="id">{{i + 1}} {{name}}</li>
  </ul>
</template>
<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>
