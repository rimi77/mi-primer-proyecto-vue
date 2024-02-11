<script setup>
const name = "Vue.js dinamico";
const stylecolor = "color:yellow";
const stylecolor1 = "color:green";
const arrayColores = ["blue", "red","green"]
const activo = true;
const sano = true;
const alegre = null;
const active = true;
const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
</script>

<template>
  <!--  Single File Components (SFC) -->

  <!-- Interpolación de texto -->
  <h1>Hello {{ name }}</h1>
  <h1>HOLA {{ name.toUpperCase() }}</h1>
  <h2 style="color:blue">I am blue</h2>

  <!-- Enlace de atributos -->
  <h1 v-bind:style="stylecolor">I am yellow</h1>
  <h1 :style="stylecolor1">I am green</h1>
  <h2>{{ arrayColores }}</h2>
  <h2 .style="`color: ${arrayColores[2]}` ">Soy verde</h2>

  <!-- Uso de expresiones de JavaScript -->
  <!-- Operador ternario -->
  <h1>
    {{ activo ? "Estoy activo" : "Estoy inactivo" }}
  </h1>

  <!-- Directivas -->
  <!-- La directiva v-if se usa para mostrar o ocultar un elemento de la plantilla. -->
  <h2 v-if="sano">Estoy sano</h2>
  <p v-if="!sano">Estoy enfermo</p>

  <!-- Directivas -->
  <!-- Un elemento v-else debe seguir inmediatamente a un v-if o un v-else-if elemento; de lo contrario, no se reconocerá. -->
  <h2 v-if="alegre === true">Estoy alegre</h2>
  <p v-else-if="alegre === false">Estoy triste</p>
  <p v-else>Estoy preocupado</p>

  <!-- Directivas -->
  <!-- La directiva v-show se usa para mostrar o ocultar un elemento de la plantilla. -->
  <h1 v-show="active">I am active (v-show)</h1>

  <!-- Directivas -->
<!-- La directiva v-for se usa para iterar sobre una lista de elementos. -->
{{ arrayFrutas }}
<ul>
  <li>{{ arrayFrutas[0]}}</li>
  <li>{{ arrayFrutas[1]}}</li>
  <li>{{ arrayFrutas[2]}}</li>
  <li>{{ arrayFrutas[3]}}</li>
  <li>{{ arrayFrutas[4]}}</li>
</ul>
<br>
<hr>

<ul>
  <li v-for="fruta in arrayFrutas">
    {{ fruta }}
  </li>
</ul>
<hr>
<br>

<ul>
  <li 
  v-for="(fruta, index) in arrayFrutas"
  :key="index">
  {{ index }} .- {{ fruta }}
</li>
</ul>
<hr>
<br>

<ul>
  <li 
    v-for="(fruta, index) of arrayFrutas"
    :key="index">
    {{ index }} .- {{ fruta }}
  </li>
  
</ul>


</template>

<style>
h1 {
  color:red;
  font-size: 70px;
  font-weight: bolder;
}
</style>