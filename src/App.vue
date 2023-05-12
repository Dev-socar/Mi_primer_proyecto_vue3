<script setup>
import {ref, computed} from 'vue'
const name = 'Primeros pasos en VUE js';
// const styleColor = "color: blue";
// const arrayColores = ['blue', 'red', 'peru'];
// const activo = false;
const arrayFrutas2 = ["🍎", "🍌", "🍉", "🍓", "🍒"];
const arrayFrutas = [
  {
      name: "Manzana",
      price: "$1.00",
      description: "Una manzana",
  },
  {
      name: "Pera",
      price: "$2.00",
      description: "Una pera",
  },
  {
      name: "Naranja",
      price: "$3.00",
      description: "Una naranja",
  },
];
const objetoFruta = {
  name: "Naranja",
  price: "$3.00",
  description: "Una naranja",
  id: 1
}
const bodegaFrutas = [
    {
        name: "Manzana",
        price: "$1.00",
        description: "Una manzana",
        stock: 0,
    },
    {
        name: "Pera",
        price: "$2.00",
        description: "Una pera",
        stock: 10,
    },
    {
        name: "Naranja",
        price: "$3.00",
        description: "Una naranja",
        stock: 20,
    },
];

//metodo
// const handleClick = (mensaje) =>{
//   console.log(mensaje);
// }
const arrayColores = ['blue', 'red'];
const counter = ref(0);
const increment = () => counter.value++;
const decrement = () => counter.value--;
const reset = () => (counter.value = 0);

const classCounter = computed(() => {
  if(counter.value === 0){
    return 'zero';
  }else if(counter.value > 0){
    return 'positive';
  }else{
    return 'negative';
  }
})

const numberFav = ref([]);
const add  = () =>{
    numberFav.value.push(counter.value);
}

const bloquearBtnadd = computed(() =>{
  const numSearch = numberFav.value.find(num => num === counter.value);
  if(numberFav.value.length === 10) return true;
  if(numSearch === 0) return true;
  return numSearch ? true : false;
})
</script>

<template>
  <h1>{{ name.toUpperCase() }}</h1>
  <br>
  <h3 :class="classCounter" class="contador">{{ counter }}</h3>
  <div class="grid">
  <button @click="increment">Aumentar</button>
  <button @click="decrement">Decrementar</button>
  <button @click="reset">Resetear</button>
  <button @click="add" :disabled="bloquearBtnadd">Agregar</button>
  </div>
  <br>
  <h3>Mis 10 números favoritos</h3>
  <ul class="favs">
    <li v-for="(favs,index) in numberFav" :key="index">
      {{ favs }}
    </li>
  </ul>

  <br>
  <hr>
  <ul>
    <legend>For array en Vuejs</legend>
    <li v-for="fruta in arrayFrutas2">
      {{ fruta }}
    </li>
  </ul>
  <br>
  <hr>
  <ul>
    <legend>Objetos en vuejs</legend>
     <li v-for="fruta in arrayFrutas" :key="fruta.name">
      {{ fruta.name }} - {{ fruta.price }} - {{ fruta.description }}
    </li>
  </ul>
  <br>
  <hr>
  <ul>
    <legend>Objeto en Vue js</legend>
    <li v-for="(value) in objetoFruta" :key="value">
       {{ value }}
    </li>
  </ul>

  <br>
  <hr>
  <ul>
    <legend>If & For juntos en Vue js</legend>
    <p>Pintamos solo elementos stock > 0</p>
    <template v-for="item in bodegaFrutas" :key="item.name">
      <li v-if="item.stock > 0" >
         {{ item.name }} - {{ item.price }}
      </li>
    </template>
  </ul>
  <br>
  <hr>





  <!-- <button @click.right.prevent="handleClick('click derecho')">Activame derecho</button>
  <button @click.middle="handleClick('click medio')">Activame centro</button>
  <button @click="handleClick('click izquierdo')">Activame izquierda</button> -->
  <!-- <h2>{{ arrayColores }}</h2>
  <h2  :style="`color: ${arrayColores[2]}`">Soy Perú</h2>
  <h2 v-if="activo === false">Estoy inactivo</h2>
  <p v-else-if="activo === true" >Estoy activo</p>
  <p v-else>Estoy indeciso</p>

  <h2 v-show="activo">Estoy activo v-show</h2> -->
</template>

<style>
h1{
  color: white;
}
.positive{
  color: green;
}
.negative{
  color: red;
}
.zero{
  color: peru;
}
.favs{
  list-style: none;
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  padding:0;
  gap: 1rem;
}
.favs li{
  text-align: center;
  font-size: 2rem;
}
.grid{
  display: grid;
  grid-template-columns: repeat(2,1fr);
  column-gap: 1rem;
  grid-template-rows: repeat(2, 2rem);
  row-gap: 1rem;
}

.grid button{
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.contador{
  font-size: 3rem;
  text-align: center;
}
</style>