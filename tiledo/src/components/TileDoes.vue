<script setup>

import Tile from './Tile.vue'

import { reactive, ref } from 'vue'

const state = reactive({
    "todos": ["0", "1", "2", "1", "2"],
    "done": ["-3 213  21lkj21 kl123kjj21k3 ", "-2", "-1", "1", "2", "1", "2"]
});

const newTodo = ref("");

const addTodo = () => {
    state.todos.push(newTodo.value);
};

const removeTodo = (index) => {
    const removedTodos = state.todos.splice(index, 1);

    addToDone(removedTodos[0]);
};

const addToDone = (todoText) => {
    state.done.push(todoText);
};

const clearHistory = () => {
    // is this allowed?
    //state.done = [];

    state.done.splice(0);
};

const clearTodos = () => {
    state.todos.splice(0);
};
</script>

<template>
  <div class="tileContainer">
      <Tile
        v-for="(todoText, index) in state.done"
        :todoText="todoText"
        :index="index"
        class="pluh"
      />
  </div>
  
  <div class="addTodoInterface">
      <input type="text" v-model="newTodo" @keyup.enter="addTodo" />

      <button @click="addTodo">
        Add todo
      </button>

      <button @click="clearHistory" :disabled="state.done.length == 0">
        Clear history
      </button>

      <button @click="clearTodos" :disabled="state.todos.length == 0">
        Clear todos
      </button>
  </div>

  <div class="tileContainer">
      <Tile
        v-for="(todoText, index) in state.todos"
        :todoText="todoText"
        @click="removeTodo(index)"
      />
  </div>

</template>

<style scoped>

.tileContainer {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
}

.tileAndButtonContainer button {
    display: block;
    margin: 1em auto;
}

.addTodoInterface {
    margin: 4em auto;
}

/*
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h3 {
    text-align: left;
  }
}
*/
</style>

