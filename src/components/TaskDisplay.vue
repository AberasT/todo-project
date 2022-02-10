<template>

    <task-list :tasks="tasks"></task-list>
    <task-form @task-added="addTask"></task-form>

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
        addTask(taskText) {
            let addedTask = {
                text: taskText,
                checked: false
            }
            this.tasks.push(addedTask);
            console.log(addedTask.text);
        }
    }
}
</script>

<style>

</style>
