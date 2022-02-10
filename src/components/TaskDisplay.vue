<template>

    <task-list :tasks="tasks"></task-list>
    <task-form @task-added="addTask(newTask)"></task-form>

</template>

<script>
import TaskForm from "./TaskForm.vue";
import TaskList from "./TaskList.vue";

export default {
    name: 'TaskDisplay',
    data() {
        return {
        tasks: []
        }
    },
    components: {
        TaskForm,
        TaskList
    },
    methods: {
        addTask(newTask) {
            this.tasks.push(newTask);
        }
    }
}
</script>

<style>

</style>
