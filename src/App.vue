<template>
  <h1>{{title}}</h1>
  <task-display></task-display>


</template>

<script>
import Task from "./components/Task";
import TaskDisplay from "./components/TaskDisplay";

export default {
    name: 'App',
    data() {
      return {
        title: 'To-Do List'
      }
    },
    components: {
      TaskDisplay
    }
}
</script>

<style>
#app {
  font-family: Helvetica;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>
