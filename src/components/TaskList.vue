<template>
    <div class="task-container">
        <p v-for="(task,index) in tasks" :key="index">{{ task.text }}</p>
    </div>
</template>

<script>

export default {
    name: 'TaskList',
    props: {
        tasks: {
            type: Array,
            required: true
        }
    }
}
</script>

<style>
    .task-container {
        background-color: rgb(175, 245, 221);
        width: 30%;
    }
</style>
