<template>
  <h1>{{title}}</h1>
  <div class="general-container">
    <div class="task-display">
      <task-display></task-display>
    </div>
    <div class="folder-container">

    </div>
  </div>
  


</template>

<script>
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

.general-container {
  width: 100%;
  display: grid;
  grid-template-columns: 50% 50%;
  justify-items: center;
}

.task-display {
  width: 100%;
  border: black solid;
  display: flex;
  flex-direction: column;
  align-items: center;
}




</style>
