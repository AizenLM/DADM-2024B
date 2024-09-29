  <script setup>
  import { ref } from 'vue'
  // Modelo
  const header = ref('App lista de compras')
  const newItem = ref('Nuevo Item')
  const newItemPriority = ref('low');
  const checkItems = ref([])
  const isPriority = ref(false)
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
    <h1>
      <i class="material-icons shopping-cart-icon">local_mall</i>
      {{ header }}
    </h1>
    <form v-on:submit.prevent="itemsList2.push({'id': itemsList2.length+1, 'name':newItem})">
    <input v-model.lazy="newItem" type="text" placeholder="Agregar articulo"> 
    <button>Agregar</button>
  
    <!-- Radio buttons---->
      <label>High<input type="radio" value="high" v v-model="newItemPriority"></label>
      <label>Low<input type="radio" value="low" v-model="newItemPriority"></label>
      {{ newItemPriority == 'high' ? '🔥': '🧊' }}
      <label for="">Pioridad: <input type="checkbox" v-model="isPriority"></label> {{ isPriority }}
      <div>
        <h3>Selecciona multiples helados</h3>
        <label>
          Chocolate
          <input type="checkbox" value="chocolate" v-model="checkItems">
        </label>
        <label>
          Valnilla
          <input type="checkbox" value="Valnilla" v-model="checkItems">
        </label>
        <label>
          Limon
          <input type="checkbox" value="Limon" v-model="checkItems">
        </label>
        <h4>Valores {{ checkItems }}</h4>
      </div>
      
    <ul>
      <li v-for="({id, name}, i) in itemsList2" :key="id">{{i + 1}} {{name}}</li>
    </ul>
  </form>
  </template>
  <style scoped>
  .shopping-cart-icon {
    font-size: 2rem;
  }
  </style>
