<template>
<div class="todo-list">
    <div 
    v-for="todo in todos"
    :key="todo.id"
    :data-value="todo.id"
    @click="toggleTodo(todo)"
    :class="{done : todo.done}"
    class="todo-item">
        {{todo.content}}
        <span class="del" @click="deleteTodo(todo)">Del</span>
    </div>
</div>
    
</template>
<script>
export default {
    props:{
        todos: Array,
    },
    methods:{
        toggleTodo(todo){
            todo.done = !todo.done
        },
        deleteTodo(index){
            this.todos.splice(index, 1);
            console.log("Delete item")
        }
    },
}
</script>

<style>
.todo-list{
    width: 100%;
    margin-top: 10px;
    max-width: 600px;
}
.todo-item{
    padding: 0px 15px;
    width: 100%;
    cursor: pointer;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    height: 50px;
    border: 1px solid rgb(216, 216, 216);
    align-items: center;
    border-radius: 5px;
}
.todo-item:hover{
    border: 1px solid rgb(146, 146, 146);
    transition: 0.3s;
}
.todo-item.done {
  color: #c4c4c4;
}
.todo-item.done:before {
  color: #c4c4c4;
  content: "";
  position: absolute;
  width: 60%;
  height: 2px;
  background: #41b883;
}

.todo-item:hover > .del {
  opacity: 1;
}

.del {
  opacity: 0;
  transition: 0.2s;
  width: 40px;
  height: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 12px;
  color: #777777;
}
.del:hover {
  background: #f7f7f7;
  color: red;
}

</style>