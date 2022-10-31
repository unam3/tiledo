<script setup>

import Tile from './Tile.vue'

import { onMounted, reactive, ref } from 'vue'


const newTodoInput = ref();

const focusNewTodoInput = () => newTodoInput.value.focus();

onMounted(() => {
    const serializedTodos = window.localStorage.getItem("todos");
    const serializedDone = window.localStorage.getItem("done");

    if (serializedTodos) {
        state.todos = JSON.parse(serializedTodos);
    }
    
    if (serializedDone) {
        state.done = JSON.parse(serializedDone);
    }
    
    focusNewTodoInput();


    window.addEventListener(
        "beforeunload",
        () => {
            window.localStorage.setItem("todos", JSON.stringify(state.todos));

            window.localStorage.setItem("done", JSON.stringify(state.done));
        }
    );
})




const state = reactive({
    "todos": ["0", "1", "2", "1", "2"],
    "done": ["-3 213  21lkj21 kl123kjj21k3 ", "-2", "-1", "1", "2", "1", "2"],
    "done": [],
    "todos": [],
    "hasPutTodoInHistory": false
});

const newTodo = ref("");

const addTodo = () => {

    if (newTodo.value != "")

        state.todos.push(newTodo.value);
};

const addTodoClick = () => {
    addTodo();
    
    // is this the way to do it right in vue?
    newTodo.value = "";

    focusNewTodoInput();
};

const putIntoHistory = (index) => {
    state.hasPutTodoInHistory = true;

    const removedTodos = state.todos.splice(index, 1);

    addToDone(removedTodos[0]);

    focusNewTodoInput();
};

const addToDone = (todoText) => {
    state.done.push(todoText);
};

const clearHistory = () => {
    // is this allowed?
    //state.done = [];

    state.done.splice(0);

    focusNewTodoInput();
};

const clearTodos = () => {
    state.todos.splice(0);

    focusNewTodoInput();
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
      <input type="text" ref="newTodoInput" v-model="newTodo" @keyup.enter="addTodoClick" />

      <button @click="addTodoClick">
        Add todo
      </button>

      <button @click="clearHistory" :disabled="state.done.length == 0">
        Clear history
      </button>

      <button @click="clearTodos" :disabled="state.todos.length == 0">
        Clear todos
      </button>
  </div>

  <div class="clickTip" v-if="!state.hasPutTodoInHistory && state.todos.length">
    Click on todo item to put it in history.
  </div>

  <div class="tileContainer">
      <Tile
        v-for="(todoText, index) in state.todos"
        :todoText="todoText"
        @click="putIntoHistory(index)"
      />
  </div>

</template>

<style scoped>

.tileContainer {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    margin: auto;
}

.tileAndButtonContainer button {
    display: block;
    margin: 1em auto;
}

.addTodoInterface {
    margin: 4em auto;
}

.clickTip {
    margin: 2em auto;
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

