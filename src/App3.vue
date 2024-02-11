<script setup>
import WelcomeItemVue from './components/WelcomeItem.vue';

const name = "Vue.js dinamico";
const arrayFrutas = [
        {
            name: "Manzana 🍎",
            price: "$1.00",
            description: "Una manzana",
        },
        {
            name: "Platano🍌",
            price: "$2.00",
            description: "Una pera",
        },
        {
            name: "Sandia🍉",
            price: "$3.00",
            description: "Una naranja",
        },
    ];

const arrayFrutas1 = ["🍎", "🍌", "🍉", "🍓", "🍒"];

const objetoFruta = {
            name: "Platano🍌",
            price: "S/. 1.00",
            description: "Cinco platanos",
            id: 1,
        }

const arrayFruit = [
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

</script>

<template>
  <h3>Hello {{ name }}</h3>
  <h3>HOLA {{ name.toUpperCase() }}</h3>

  <!-- Directiva "v-for" - Practica -->
<!-- La directiva v-for se usa para iterar sobre una lista de elementos. -->

<hr>
<br>

<ul>
  <li 
  v-for="(fruta, i) of arrayFrutas1"
  :key="p">
  {{ i }} .- {{ fruta }}
</li>
</ul>

<hr>
<br>

<ul>
  <li 
  v-for="(fruta, i) of arrayFrutas"
  :key="p">
  {{ i }} .- {{ fruta.name }} - {{ fruta.price }} - {{ fruta.description }} 
</li>
</ul>

<hr>
<br>
{{ objetoFruta }}
<br>
<br>

<hr>
<br>

<ul>
  <li v-for="(value, propiedad, index) in objetoFruta" :key="value">
    {{ index }} .- {{ propiedad }} : {{ value }}
  </li> 
  
</ul>

<hr>
<br>
<!-- Directiva "v-for v-if" - Practica -->
<!-- Cuando existen en el mismo nodo, v-if tiene una prioridad más alta que v-for. Eso significa que la condición v-if no tendrá acceso a las variables del alcance de v-for:. -->

<ul>
  <template v-for="fruta in arrayFruit" :key="fruta.name">
    <li v-if="fruta.stock > 0">{{ fruta.name }} - {{ fruta.price }}</li>
  </template>
  
</ul>
<br>

<hr>
<br>

</template>

<style>
h3 {
  color:red;
  font-size: 30px;
  font-weight: bolder;
}
</style>