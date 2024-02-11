<script setup>
import { ref, computed  } from 'vue';
/* "ref" es para aplicar "reactvidad" y "computed" para "propiedades computadas" */

const name = "Vue.js dinamico";

// Con Propiedades Computadas - Añadir numeros generados a un array

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

// Con Propiedades Computadas - Añadir numeros generados a un array, pero que no sean repetidos

const counter1 = ref(0);

/*  se inicializa con un array vacio */
const arrayFavoritos1 = ref([]);

const increase1 = ()=> {
  counter1.value ++;
}

const decrease1 = ()=> {
  counter1.value --;
}

const reset1 = ()=> {
  counter1.value = 0;
}

const add1 = () => {
  arrayFavoritos1.value.push(counter1.value)
}

const blockBtnAdd = computed(() => {
  const numSearch = arrayFavoritos1.value.find((num1) => num1 === counter1.value)
  console.log(numSearch)
  if (numSearch === 0) return true;
  return numSearch ? true : false;

})

const classCounter1 = computed(()=> {
  if(counter1.value === 0){
    return 'zero'
  }
  if(counter1.value > 0){
    return 'green'
  }
  if(counter1.value < 0){
    return 'red'
  }
})

</script>

<template>
    <h3>HOLA {{ name.toUpperCase() }}</h3>
    <br>
    <!-- Añadir numeros generados a un array -->
    <h2>Aplicando Propiedades Computadas</h2>
    <h2>Añadir numeros generados a un array</h2>
    <br>
    <h3 v-bind:class="classCounter">{{ counter }}</h3>
    <button @click="increase">Increase</button>
    <button @click="decrease">Decrease</button>
    <button @click="reset">Reset</button>
    <button @click="add">Add</button>
    <br>
    {{ arrayFavoritos }}
    <ul>
      <li v-for="(num, i) in arrayFavoritos" :key="i">
        {{ num }}
      </li>
    </ul>

    <br>
    <!-- Añadir numeros generados a un array, pero que no sean repetidos -->
    <h2>Aplicando Propiedades Computadas</h2>
    <h2>Añadir numeros generados a un array, pero que no sean repetidos</h2>

    <br>
    <h3 v-bind:class="classCounter1">{{ counter1 }}</h3>
    <button @click="increase1">Increase</button>
    <button @click="decrease1">Decrease</button>
    <button @click="reset1">Reset</button>
    <button @click="add1" :disabled="blockBtnAdd">Add</button>
    <br>
    {{ arrayFavoritos1 }}
    <ul>
      <li v-for="(num1, i) in arrayFavoritos1" :key="i">
        {{ num1 }}
      </li>
    </ul>

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