<script setup>
  const name = "Hector"
  const styleColor = "color: blue"
  const arrayColors = ["blue", "red", "orange"]
  const activo = false
  const arrayFrutas = [
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

const clic = () =>{
  console.log("clic")
}
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <h1>{{ arrayColors }}</h1>
  <h1 :style="styleColor">xd</h1>
  <h1 :style="`color: ${arrayColors[1]}`">xd</h1>
  <h2>{{ activo ? "Estoy activo" : "Estoy inactivo" }}</h2>
  <h2 v-if="activo === true">Estoy activo</h2>
  <p v-else-if="activo === false">Estoy inactivo</p>
  <p v-else>Estoy indeciso</p>
  <h1 v-show="activo">Estoy activo v-show</h1>
  <ul>
    <!--Si estan en la misma etiqueta, v-if vale más que v-for, o sea siempre se va ejecutar primero -->
    <!--la key es para ayudar a vue, no es recomendable pasar el index como key, es mejor pasarle el id (esto haciendo referencia a cuando tenemos objetos con su respectivo identificador) -->
    <li v-for="(color, index) in arrayColors" :key="index">
      {{index}} - {{ color }}
    </li>
  </ul>
  <ul>
    <li v-for="element in arrayFrutas" :key="element.name">La {{ element.name }} vale {{ element.price }}. Descripción: {{ element.description }}</li>
  </ul>
  <ul>
    <li v-for="(value, propiedad, index) in fruta" :key="index">{{index}} - {{propiedad}}: {{ value }}</li>
  </ul>
  <ul>
    <template v-for="element in arrayFrutas" :key="element.name">
      <li v-if="element.stock > 0">{{ element.name }}</li>
    </template>
  </ul>
  <button @click="clic">Activame</button>
  <button @click.right="clic">Activame right</button>
</template>

<style>
  h1{
    color: red
  }
</style>