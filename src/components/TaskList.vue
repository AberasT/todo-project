<template>
    <div class="task-container" v-for="(task,index) in tasks" :key="index">
        <p class="p-task" >{{ task.text }}</p>
        <div class="task-buttons">
            <button class="button" @click="onEdit(index,task)">Edit</button>
            <button class="button" @click="removeTask(index)">Remove</button>
            <input class="checkbox" type="checkbox" >
        </div>
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
    },
    methods: {
        onEdit(index,task) {
            this.$emit("edit-submitted",index,task);
        }
    }
}
</script>

<style>
    .task-container {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
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

    .task-buttons {
        display: flex;
        flex-direction: row;
        align-items: center;
    }
    .checkbox {
        cursor: pointer;
        margin-right: 12px;
    }


</style>
