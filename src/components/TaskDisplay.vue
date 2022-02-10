<template>

    <task-list :tasks="tasks"></task-list>
    <task-form @task-added="addTask" @task-edited="editTask"></task-form>

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
        },
        editTask(index,editedTask) {
            let replaceTask = {
                text: editedTask,
                checked: false
            }
            this.tasks[index] = replaceTask;
        }
    }
}
</script>

<style>

</style>
