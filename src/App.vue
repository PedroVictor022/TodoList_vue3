<template>
  <TodoApp />
</template>

<script>
import TodoApp from './component/TodoApp.vue';
export default {
  components: {
    TodoApp,
  }
}
</script>


<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  background: #222;
  font-family: sans-serif;
  padding-bottom: 1em;
  width: 80%;
  margin: 0 auto;

}
</style>
