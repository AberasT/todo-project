<template>
    <div class="task-container done-task-container" v-for="(task,index) in doneTasks" :key="index">
        
        <p class="p-task done-task" >
            <button 
                class="button  done-button" 
                @click="$emit('not-done-submitted',index)">
                Not Done!
            </button>   
            {{ task.text }}</p>
        <div class="task-buttons">
            <button 
                class="button color-red" 
                @click="$emit('remove-done-submitted',index)">
                Remove
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'DoneTaskList',
    emits: ['remove-done-submitted','not-done-submitted'],
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
    .done-task-container {
        justify-content: space-between;
        background-color: rgb(241, 241, 241);
        box-shadow: 5px 4px 2px rgb(200, 200, 200);
    }
</style>
