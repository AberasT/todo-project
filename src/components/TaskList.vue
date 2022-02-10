<template>
    <div class="task-container" v-for="(task,index) in tasks" :key="index">
        <p class="p-task" >{{ task.text }}</p>
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
        background-color: rgb(246, 246, 246);
        width: 70%;
        margin: 10px;
        text-align:initial;
        border: rgb(53, 174, 255) solid;
        box-shadow: 5px 4px 2px gray;
    }

    .p-task {
        font-family: 'Poppins', sans-serif;
        font-weight: 600;
        margin: 5px 40px;
        color: #19232e;
    }
</style>
