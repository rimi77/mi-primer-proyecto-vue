<script setup>
import { ref, computed  } from 'vue';
/* "ref" es para aplicar "reactvidad" y "computed" para "propiedades computadas" */

const name = "Vue.js dinamico";


// Con Propiedades Computadas - Añadir numeros generados a un array, pero que no sean repetidos

const counter = ref(0);

/*  se inicializa con un array vacio */
const arrayFavoritos = ref([]);

const increase = ()=> {
  counter.value ++;
}

const decrease = ()=> {
  counter.value --;
}

const reset = ()=> {
  counter.value = 0;
}

const add = () => {
  arrayFavoritos.value.push(counter.value)
}

const blockBtnAdd = computed(() => {
  const numSearch = arrayFavoritos.value.find((num) => num === counter.value)
  console.log(numSearch)
  if (numSearch === 0) return true;
  return numSearch ? true : false;

})

const classCounter = computed(()=> {
  if(counter.value === 0){
    return 'zero'
  }
  if(counter.value > 0){
    return 'green'
  }
  if(counter.value < 0){
    return 'red'
  }
})

</script>

<template>
  <div class="container text-center mt-3">
    <h3>HOLA {{ name.toUpperCase() }}</h3>
    <br>
    <!-- Añadir numeros generados a un array, pero que no sean repetidos -->
    <h2>Aplicando Propiedades Computadas</h2>
    <h2>Añadir numeros generados a un array, pero que no sean repetidos</h2>
    <br>
    <h3 v-bind:class="classCounter">{{ counter }}</h3>
    <div class="btn-group">
      <button @click="increase" class="btn btn-success">Increase</button>
      <button @click="decrease" class="btn btn-danger">Decrease</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="blockBtnAdd" class="btn btn-primary">Add</button>
    </div>
    <ul class="list-group">
      <li class="list-group-item" v-for="(num, i) in arrayFavoritos" :key="i">
        {{ num }}
      </li>
    </ul>
  </div>

</template>

<style>
h3 {
  color: orange;
  font-size: 30px;
  font-weight: bolder;
}
h2 {
  color: blue;
  font-size: 20px;
  font-weight: bolder;
}

.green {
  color: green;
}

.red {
  color: red;
}

.zero {
  color:mediumpurple;
}
</style>