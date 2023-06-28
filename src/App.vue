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
  
  <div class="container">
    <div>
      <h2 :style="`color:${stateColor}`" >
        Contador: {{ veces }}
      </h2>
    </div>
    <button @click="actualizarContador(+1)">+1</button>
    <button @click="actualizarContador(-1)">-1</button>
    <button @click="actualizarContador(0)">Resetear</button>
    <button @click="add" :disabled="incluido">Add</button>
    
  </div>
  <div class="container">
    <h3>Lista de números favoritos:</h3>
    <ul>
      <li v-for="(number,index) in favoritos" :key="index">
        {{ number }}
      </li>
    </ul>
  </div>
</template>


<style >
  h4
  h1{
    color: red;
  }
  button{
    padding: 5px 10px;
    
    border: 1px solid rgb(255, 255, 255);
    background-color: rgb(33, 184, 33);
    border-radius: 5px;
    margin: 10px 0px;
    max-width: 200px;
  }
  .container{
    display: flex;
    flex-direction: column;
    border:  1px solid silver;
    padding: 15px ;
    border-radius: 5px;
    margin: 5px;
    
  }
  
</style>