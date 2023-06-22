<script setup>
import { ref, computed } from "vue";

const arr = ref([]);

const counter = ref(0);

const increment = () => {
  counter.value++;
};

const decrement = () => {
  counter.value--;
};

const reset = () => {
  counter.value = 0;
};

const comprobar = computed(() => {
  const find = arr.value.find((n) => n == counter.value);
  return find || find === 0;
});

const add = () => {
  arr.value.push(counter.value);
};

const classCounter = computed(() => {
  if (counter.value === 0) {
    return "zero";
  }
  return counter.value > 0 ? "positive" : "negative";
});
</script>

<template>
  <div class="container text-center">
    <h2 :class="classCounter">
      {{ counter }}
    </h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Incremet</button>
      <button @click="decrement" class="btn btn-danger">Decrement</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="comprobar" class="btn btn-primary">
        Add
      </button>
    </div>

    <ul class="list-group mt-4">
      <li v-for="(fav, i) in arr" :key="i" class="list-group-item">{{ fav }}</li>
    </ul>
  </div>
</template>

<style>
.negative {
  color: red;
}

.positive {
  color: green;
}

.zero {
  color: black;
}
</style>
