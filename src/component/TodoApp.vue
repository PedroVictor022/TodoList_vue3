<template>
   <div class="container">
      <h2 class="title-app">Vue3 Todo App</h2>
      <form @submit="addNewTodo">
         <label>New Todo</label>
         <input type="text" name="newTodo" v-model="newTodo">
         <button>Add New Todo</button>

         <ul class="todos" v-for="(todo, index) in todos" :key="todo.id">
            <li @click="toggleDone(todo)" :class="{ done: todo.done }">{{ todo.content }}</li>
            <button @click="removeTodo(index)">Delete Todo</button>
         </ul>

         <button
            type="button"
            @click="markAllDone"
         >Complete all todos</button>


      </form>

   </div>
</template>

<script>
import { ref } from 'vue';
export default {

   name: "TodoApp",
   setup() {
      const newTodo = ref("");
      const todos = ref([]);

      function generateId() {
         return Math.floor(Math.random() * 1000).toFixed(2)
      }

      function addNewTodo(e) {
         e.preventDefault();

         todos.value.push({
            id: generateId(),
            done: false,
            content: newTodo.value
         });

         console.log(newTodo.value);
         newTodo.value = "";
      }

      function toggleDone(todo) {
         todo.done = !todo.done
         console.log(todo.done ? "Complete" : "No Complete")
      }

      function removeTodo(index) {
         todos.value.splice(index, 1);
      }
      
      function markAllDone() {
         todos.value.forEach((todo) => todo.done = true)
      }

      // Ao usar setup() temos que 'expor os dados retornados por ele, usando o return'
      return {
         todos,
         newTodo,
         addNewTodo,
         toggleDone,
         removeTodo,
         markAllDone
      }
   }
}
</script>

<style>
body {
   background: #222;
   color: #fefefe;
   font-family: sans-serif;
   padding-top: 1em;
   padding-bottom: 1em;
   width: 60%;
   margin: 0 auto;
}

input,
textarea,
button,
p,
div,
section,
article,
select {
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