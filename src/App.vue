<template>
  <h1>{{title}}</h1>
  <div class="task-display">
    <task-display></task-display>
  </div>

</template>

<script>
import TaskDisplay from "./components/TaskDisplay";

export default {
    name: 'App',
    data() {
      return {
        title: 'My To-Do List'
      }
    },
    components: {
      TaskDisplay
    }
}
</script>

<style>
#app {
  font-family: 'Poppins';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

h1 {
  text-decoration: underline;
  font-weight: 500;
  text-shadow: 2px 1px 1px rgb(177, 177, 177);
}

.task-display {
  width: 100%;
}

</style>
