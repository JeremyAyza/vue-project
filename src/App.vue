<script setup>
import { ref, computed } from 'vue';

  const veces=ref(0)
  const favoritos=ref([])

  const actualizarContador=(x)=> {
    if(x===0) veces.value=0 
    else veces.value+=x
    console.log(veces.value);
    console.log({stateColor});
  };
  const add=()=>{
    favoritos.value.push(veces.value)
  }
  
  const stateColor= computed(() =>veces.value>0?"green":veces.value<0? "red":null)
  const incluido= computed(() =>favoritos.value.includes(veces.value))
  
</script>

<template>
  <div>
    <h4 :style="`color:${stateColor}`" >
      Cantidad de clicks: {{ veces }}
    </h4>
  </div>
  <br>
  <div>
    <button @click="actualizarContador(+1)">+1</button>
    <button @click="actualizarContador(-1)">-1</button>
    <button @click="actualizarContador(0)">Resetear</button>
    <button @click="add" :disabled="incluido">Add</button>
    <ul>
      <li v-for="(number,index) in favoritos" :key="index">
        {{ number }}
      </li>
    </ul>


  </div>
</template>


<style >
  h1{
    color: red;
  }
  .card{
    background-color: rgb(222, 222, 222);
    padding: 10px;
    border-radius: 5px;
    margin: 10px 0px;
  }
</style>