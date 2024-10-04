<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
// ---Items---
const items = ref([
    {id:'0', label: '10 bolillos'}, 
    {id:'1', label: '1 lata de volt'}, 
    {id:'2', label: '1 bote de café'},
    {id:'3', label: '10 chetos'}
]);
//Item-Method
const saveItem = () => {
    //Agregamos otro item
    items.value.push({id: items.value.length + 1, label: newItem.value});
    //queda vacia la caja de texto
    newItem.value = '';
    
}
// --- Formulario ---
const newItem = ref(''); 
const newItemHighPriority = ref(false);
const editing = ref(true);
const activareEdition = (activate) => {
    editing.value = activate;
}
</script>


<template>

<div class="header">
<h1>
    <i class="material-icons shopping-cart-icon"
    >local_mall</i>
    {{ header }} <span style="color: blueviolet;"> {{ newItemHighPriority }} </span> 
</h1>

<button v-if="editing" class="btn" @click="activareEdition(false)">Cancelar</button>
<button v-else class="btn btn-primary" @click="activareEdition(true)">Agregar articulo</button>
</div>


<!-- Agrupando en un div las entradas -->
<form class="add-item form" 
v-if="editing"
v-on:submit.prevent="saveItem">
    
    <!-- entrada de texto -->
    <input
      v-model.trim="newItem"
      type="text"
      placeholder="Add Item">
    
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      Alta prioridad
    </label>

    <!-- Boton -->
    <button class="btn btn-primary"> Guardar </button>
  
</form>
    <!-- Lista de items -->
    <ul>
        <li v-for="({id,label}, i) in items" :key="id"> {{ i+1 }} {{i%2==0?'🔥':'🛍️'}} {{label}} </li>
    </ul>
    <p v-if="items.length === 0">😵 NO HAY ELEMENTOS EN LA LISTA</p>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>