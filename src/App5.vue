<script setup>
import { ref, computed  } from 'vue';
/* "ref" es para aplicar "reactvidad" y "computed" para "propidades computadas" */
const name = "Vue.js dinamico";

  //metodo - methods
  const handleClick = (message) => {
    console.log(message);
  };
  
  // Sin aplicar Reactividad, incrementa en la consola pero no en el DOM
  let counter = 0;
  
  const increase = ()=> {
    counter++;
    console.log(counter);
  }
  
  // con Reactividad
const counter1 = ref(0);

const increase1 = ()=> {
  counter1.value ++;
}

const decrease = ()=> {
  counter1.value --;
}

const reset = ()=> {
  counter1.value = 0;
}

// Con Propiedades Computadas

const counter2 = ref(0);

const increase2 = ()=> {
  counter2.value ++;
}

const decrease2 = ()=> {
  counter2.value --;
}

const reset2 = ()=> {
  counter2.value = 0;
}

const classCounter = computed(()=> {
  if(counter2.value === 0){
    return 'zero'
  }
  if(counter2.value > 0){
    return 'green'
  }
  if(counter2.value < 0){
    return 'red'
  }
})

</script>

<template>
    <h3>HOLA {{ name.toUpperCase() }}</h3>
<!-- Directiva "v-on" - Modificadores de Eventos -->
    <h2>Modificadores de Eventos</h2>
    <button v-on:click="handleClick('Text Right')">Activate right</button>
    <button v-on:click.right.prevent="handleClick('Text Right')">Desactivate right</button>
    <button @click="handleClick('Text Left')">Activate left</button>
    <button @click="handleClick('Text Middle')">Activate middle</button>
    <br>
    <br>
    <hr>
    <!-- Sin aplicar Reactividad  -->
    <hr>
    <h2>Sin aplicar Reactividad</h2>
    <br>
    <h3>{{ counter }}</h3>
    <button @click="increase">Increase</button>
    
    <br>
    <br>
    <hr>
    <!-- Aplicando Reactividad  -->
    <hr>
    <h2>Aplicando Reactividad</h2>
    <br>
    <h3 v-bind:class="counter1  > 0 ? 'green' : 'red'">{{ counter1 }}</h3>
    <button @click="increase1">Increase</button>
    <button @click="decrease">Decrease</button>
    <button @click="reset">Reset</button>

    <br>
    <br>
    <hr>
    <!-- Aplicando Propiedades Computadas  -->
    <!-- Las propiedades computadas nos sirven para generar calculos en nuestros componentes -->
    <hr>
    <h2>Aplicando Propiedades Computadas</h2>
    <br>
    <h3 v-bind:class="classCounter">{{ counter2 }}</h3>
    <button @click="increase2">Increase</button>
    <button @click="decrease2">Decrease</button>
    <button @click="reset2">Reset</button>

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