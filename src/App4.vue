<script setup>
import WelcomeItemVue from './components/WelcomeItem.vue';

const name = "Vue.js dinamico";

const arrayFrutas1 = ["🍎", "🍌", "🍉", "🍓", "🍒"];

const arrayFruit = [
    {
        name: "Manzana 🍎",
        price: "S/. 5.00",
        description: "Dos manzanas",
        stock: 0,
    },
    {
      name: "Fresa 🍓",
      price: "S/. 7.00",
      description: "Un kilo de fresa",
      stock: 1,
    },
    {
      name: "Platano 🍌",
      price: "S/ 3.00",
      description: "Cinco platanos",
      stock: 5,
    },
  ];

  //metodo - methods
  const handleClick = (message) => {
    console.log(message);
  };
  
</script>

<template>
    <h3>HOLA {{ name.toUpperCase() }}</h3>
    
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
  
<!-- Directiva "v-on" - Eventos -->
<!-- Podemos usar la directiva v-on, que normalmente acortamos al símbolo @, para escuchar eventos DOM y ejecutar JavaScript cuando se activan. El uso sería v-on:click="handler" o con el atajo, @click="handler". -->

    <button v-on:click="handleClick('Mensaje 1')">Activame</button>
    <button @click="handleClick('Mensaje 2')">Active the button</button>
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