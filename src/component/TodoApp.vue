<template>
   <div class="container">
      <h2 class="title-app">Vue3 Todo App</h2>
      <form @submit="addNewTodo">
         <label>New Todo</label>
         <input type="text" name="newTodo" v-model="newTodo">
         <button>Add New Todo</button>

         <div class="todos">
            <p>{{ newTodo }}</p>
         </div>
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

      function addNewTodo(e) {
         e.preventDefault();
         console.log(newTodo.value);
         todos.value.push({
            done: false,
            content: newTodo.value
         });
      }

      // Ao usar setup() temos que 'expor os dados retornados por ele, usando o return'
      return {
         todos,
         newTodo,
         addNewTodo,
      }
   }
}
</script>

<style>
.container {
   margin: 0 auto;
   width: 420px;

   display: flex;
   flex-direction: column;
   align-items: center;
   justify-content: center;
}

.title-app {
   font-size: 36px;
   background: -webkit-linear-gradient(#b7f54c, #049674);
   -webkit-background-clip: text;
   -webkit-text-fill-color: transparent;

   margin-top: 2rem;
   margin-bottom: 1rem;
}

form {
   display: flex;
   flex-direction: column;
   gap: 0.8rem;

   padding: 1rem;
   border-radius: 6px;

   background: #141414;

   width: 320px;
}

label {
   font-size: 22px;
   color: #fefefe;
}

input {
   width: 100%;
   padding: 0.2rem;
   border: none;
   outline: none;
   border-radius: 4px;
}

button {
   cursor: pointer;
   width: 100%;
   padding: 0.2rem;
   border-radius: 4px;
   background: linear-gradient(#b7f54c, #049674);
   font-weight: 700;
   color: #141414;
   font-size: 14px;
   transition: all .2s;
}

button:hover {
   transition: .2s;
   background: linear-gradient(#b9e66d, #049674);
}
</style>