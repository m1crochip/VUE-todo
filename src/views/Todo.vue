<template>
  <div class="todo-page">
    <h3>Todopage</h3>
    <form @submit.prevent="addNewTodo">
      <input placeholder="Please Type some thing...." v-model="newTodo">
      <button type="submit">Add</button>
    </form>
    <Todolist :todos="todos"/>
  </div>
</template>

<script>
import Todolist from '../components/Todolist.vue';

export default {
  components:{
    Todolist,
  },
  data() {
    return{
      todos:[],
      newTodo:"",
    }
  },
  methods: {
    addNewTodo(){
      this.todos.push({
        id:Date.now(),
        done: false,
        content: this.newTodo
      });
      console.log(this.todos);
      this.newTodo = "";
    }
  },
}
</script>

<style>
.todo-page {
  width: 100%;
  display: flex;
  padding-top: 160px;
  flex-direction: column;
  align-items: center;
}

</style>