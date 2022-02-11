<template>
    <div class="task-container" v-for="(task,index) in doneTasks" :key="index">
        <p class="p-task done-task" >{{ task.text }}</p>
        <div class="task-buttons">
            <button 
                class="button" 
                @click="$emit('remove-done-submitted',index)">
                Remove
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'DoneTaskList',
    emits: ['remove-done-submitted'],
    props: {
        doneTasks: {
            type: Array,
            required: true
        }
    },
    methods: {
    }
}
</script>

<style>
    .done-task {
        text-decoration: line-through;
        color: rgb(93, 93, 93);
    }
</style>
