
<!-- <script setup>

const name = "vue dinamico";
const styleColor = "color: blue";


const arrayFrutas = [
        {
            name: "Manzana",
            price: "$1.00",
            description: "Una manzana",
            stock: 6,
        },
        {
            name: "Pera",
            price: "$2.00",
            description: "Una pera",
            stock: 9,
        },
        {
            name: "Naranja",
            price: "$3.00",
            description: "Una naranja",
            stock: 2,
        },

    ];


  const miObjeto = {
            name: "Sandia",
            price: "$3.00",
            description: "Una sandia",
  }


</script>

<template>
  <h1>Hola {{ name }}</h1>
  <h2 :style="styleColor">mi color es azul</h2>


  <h2>Ejemplo de v-for para recorrer un arreglo [ ]</h2>
  <ul>
    <li
    v-for="fruta in arrayFrutas"
    :key="fruta.name"
    >
    {{ fruta.name }} - {{ fruta.price }} - {{ fruta.description }}
    </li>
  </ul>


  <h2>Ejemplo de v-for para recorrer un objeto { }</h2>
  <ul>
    <li
     v-for="(value, propiedad, index) in miObjeto"
     :key="value"
    >
    {{ index }} - {{ propiedad }} : {{ value }}
    </li>
  </ul>

  <h2>Ejemplo usando un v-for y un v-if anidado</h2>

  <template 
    v-for="item in arrayFrutas"
    :key="item.name"
  >
    <h1 v-if="item.stock > 5">
      {{ item.name }} - {{ item.stock }}
    </h1>
  </template>





</template>

<style>
h1{
  color: red;
}
</style> -->


<script setup>
import { ref, computed} from 'vue';
import BlogPost from './components/BlogPost.vue';

const contador = ref(0)

const increment = () => {
  contador.value++
}

const decrement = () => {
  contador.value--
}


const reset = () => {
  contador.value = 0
}

const classCounter = computed( () => {
  if(contador.value === 0) return 'zero'
  if(contador.value > 0) return 'positive'
  if(contador.value < 0) return 'negative'
})


const fav = ref([])

const add = () => {
    fav.value.push(contador.value)
}


const blockButton = computed ( () => {
  //const numSearch = fav.value.find( (num) => num === contador.value)
  const numSearch = fav.value.includes(contador.value)
  return numSearch ? true : false
})


</script>


<template>

  <div class="container text-center mt-3">

    <h2 :class="classCounter" >{{ contador }}</h2>

    <div class="btn-group">
      <button @click="decrement" class="btn btn-danger">Decrementar</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="increment" class="btn btn-success">incrementar</button>
      <button @click="add" :disabled="blockButton" class="btn btn-primary">Agregar a lista</button>
    </div>

    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="(item, index) in fav" :key="index" >
          {{ item }}
      </li>
    </ul>

    <BlogPost title="Post 1" id="1" body="Descripcion 1" colorText="primary"></BlogPost>
    <BlogPost title="Post 2" id="2" body="Descripcion 2" colorText="secondary"></BlogPost>
    <BlogPost title="Post 3" id="3" body="Descripcion 3" colorText="success"></BlogPost>
  </div>




</template>


<style>

.positive{
  color: green;
}

.negative{
  color: red;
}

.zero{
  color: yellow
}

</style>