<script setup>

import Tile from './Tile.vue'

import { reactive } from 'vue'

const state = reactive({"todos": ["pluh", "meh"]});

const addTodo = function(todo) {
    state.todos.push(newTodo.value);
};

</script>

<template>
  <Tile
    v-for="(todoText, index) in state.todos"
    :todoText="todoText"
    :index="index"
  />

  <input v-model="newTodo" />

  <button @click="addTodo">
   Add todo
  </button>
</template>

<style scoped>

.tile {
  min-height: 10em;
  min-width: 16em;
  border-radius: 0.5em;
  border: 1px solid black;
}

.tileAndButtonContainer textarea {
  display: block;
  min-height: 10em;
  min-width: 16em;
  margin: 0;
  text-align: center;
  border: 2px solid #a94646;
  border-radius: 0.5em;
}

.tileAndButtonContainer button {
    display: block;
    margin: 1em auto;
}

.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h3 {
    text-align: left;
  }
}
</style>

