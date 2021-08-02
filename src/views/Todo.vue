<template>
  <h1>Vue Todo</h1>
  <form @submit.prevent="addNewTodo">
    <lable>Input Your List</lable>
    <input v-model="newTodo" name="newTodo">
    <button>Add new Todo</button>
  </form>
  <ul>
  <li v-for="todo in todos" :key="todo.id">
    <h3 :class="{done : todo.done}" @click="toggleDone(todo)" class="todo">{{todo.content}}</h3>
    <button @click="removeTodo(index)">remove</button>
  </li>
  </ul>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const newTodo = ref('')
    const todos = ref([]);

    function addNewTodo() {
      todos.value.push({
        id: Date.now(),
        done: false,
        content : newTodo.value,
      });
      newTodo.value = '';
    }

    function toggleDone(todo) {
      todo.done = !todo.done;
    }

    function removeTodo(index) {
      todos.value.splice(index, 1);
    }
    return {
      todos,
      newTodo,
      addNewTodo,
      toggleDone,
      removeTodo,
    }
  }
}
</script>

<style>
body {
  font-family: sans-serif;
  padding-top: 1em;
  padding-bottom: 1em;
  font-size: 2em;
  width: 80%;
  margin: 0 auto;
}
input, textarea, button, p, div, section, article, select {
  display: 'block';
  width: 100%;
  font-family: sans-serif;
  font-size: 1em;
  margin: 0.5em;
}
.todo {
  cursor: pointer;
}
.done {
  text-decoration: line-through;
}
</style>