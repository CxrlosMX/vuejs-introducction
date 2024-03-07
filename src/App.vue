<script setup>

const name = 'Vue Js 3.0';

const styleColor = 'color: brown';

const greeting = 'Soy Rendon el guapo';

const arrayColors = ['red', 'blue', 'peru'];

const active = !true;

const arrayFruits = ['🍇', '🥭', '🍎', '🍉', '🍍', '🍒', '🍐'];

const arrayObjects = [
  {
   
   
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    emoji: "🍎",
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
    emoji: "🍐",
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
    emoji: "🥭",
  }];

  const object= {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    emoji: "🍎",
    id: 1,
  };
  const arrayObjectsFruits=[
  {
   name: "Manzana",
   price: "$1.00",
   description: "Una manzana",
   emoji: "🍎",
   stock: 10,
 },
 {
   name: "Pera",
   price: "$2.00",
   description: "Una pera",
   emoji: "🍐",
   stock: 15,
 },
 {
   name: "Naranja",
   price: "$3.00",
   description: "Una naranja",
   emoji: "🥭",
   stock: 8,
 }
  ];
  const persons=[
  {
   name: "Luis",
   lastName: "Rendon",
   description: "Persona alta",
   age: 23,
 },
 {
   name: "Sayuri",
   lastName: "Rendon",
   description: "Persona alta",
   age: 23,
 },
 {
   name: "Jesus",
   lastName: "Martinez",
   description: "Persona alta",
   age: 23,
 },
  ];

  const handlerClick=()=>{
    console.log("Le diste click al boton");
  }
  const handlerClick02=(message)=>{
    console.log(message);
  }
</script>

<template>
  <h1>Hola {{ name }}</h1>
  <br>
  <h2 v-bind:style="styleColor">{{ greeting.toUpperCase() }}</h2>
  <br>
  <h2>{{ arrayColors }}</h2>
  <br>
  <h2 v-bind:style="`color: ${arrayColors[2]}`">Hola soy color azul</h2>
  <br>
  <h2> {{ active ? 'Hola, estoy activo' : 'Adios, estoy inactivo' }}</h2>
  <br>
  <h2 v-if="active">Estoy utilizando: v-if</h2>
  <h2 v-else-if="!active">Estoy utilizando: v-else-if</h2>
  <h2 v-else>Estoy utilizando: v-else</h2>
  <br>
  <h2 v-show="!active">Estoy utilizando: v-show</h2>
  <br>
  <h2>Array Frutas - Usando v-for</h2>
  <p>{{ arrayFruits }}</p>
  <p>Recorriendo un array con v-for</p>
  <br>
  <ul>
    <li v-for="i in arrayFruits">
      {{ i }}
    </li>
  </ul>
  <br>
  <ul>
    <li v-for="(i, index) in arrayFruits" :key="index">
      {{ index }} - {{ i }}
    </li>
  </ul>
  <br>
  <h2>Recorriendo array de objetos con v-for</h2>
  <br>
  <ul>
    <li v-for="(i, index) in arrayObjects" :key="i.name">

      Nombre: {{ i.name }}
      - Descripción: {{ i.description }}
      - Precio: {{ i.price }}
      - Emoji: {{ i.emoji }}

    </li>
  </ul>
  <br>
  <h2>Recorriendo un Objeto con "v-for"</h2>
  <br>
  <ul>
    <li v-for="(valor, campo, index) in object" :key="index">
       {{ index }}: {{ campo }} : {{ valor }} 
       <!-- 53:52 -->
    </li>
  </ul>
  <br>
  <h2>V-FOR AND V-IF - Usando ambos, recorriendo un arreglo con condicionales</h2>
  <br>
  <ul>
    <template v-for="i in arrayObjectsFruits" :key="i.name">
          
      <li v-if="i.stock >10">     {{ i.name }} - {{ i.emoji }} </li>
    </template>
  </ul>
 <br>
 <h2>Recorriendo arreglos con v-for y condiciones con v-if</h2>
 <br>
 <ul>
  <template v-for="item in persons" :key="item.name">
    
    <li v-if="(item.lastName)==='Rendon'">
      {{ item.name }}

    </li>  
    
  </template>
 </ul>
 <br>
  <h2>Botones en VueJS</h2>
  <br>
  <button v-on:click="handlerClick">Hola soy un boton 01</button>
  <button @click="handlerClick">Hola soy un boton 02</button>

  <h2>Botones con mensajes dinamicos y funcion segun el click que des - el mensaje se pasa como parametro</h2>
  <br>
  <button v-on:click.right.prevent="handlerClick02('Boton Right')">Boton Right</button>
  <button @click="handlerClick02('Boton Left')">Boton Left</button>
  <button @click.middle="handlerClick02('Boton Middle')">Boton Middle</button>
 </template>
<style>
h1 {
  color: antiquewhite;
}
button{
  color: black;
  background-color: aqua;
  border-radius: 1%;
}
</style>