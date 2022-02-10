<template>
  <h1>{{title}}</h1>
  <ul>
    <li v-for="(task,index) in tasks" :key="index">{{task}}</li>
  </ul>
  <input type="text">
  <button @click="addTask">Add</button>

</template>

<script>
import Task from "./components/Task";

export default {
  name: 'App',
  data() {
    return {
      title: 'To-Do List',
      tasks: ['1','2','3']
    }
  },
  components: {
    Task
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
