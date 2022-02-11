<template>
    <div class="task-container" v-for="(task,index) in tasks" :key="index">
        <p class="p-task">
            <button 
                class="button  done-button" 
                @click="$emit('done-submitted',index)">
                Done!
            </button>
            {{ task.text }}
        </p>
        <div class="task-buttons">
            <button 
                class="button color-blue" 
                @click='$emit("edit-submitted",index,task)'>
                Edit
            </button>
            <button 
                class="button  color-red" 
                @click="$emit('remove-submitted',index)">
                Remove
            </button>
            
        </div>
    </div>
</template>

<script>

export default {
    name: 'TaskList',
    emits: ['edit-submitted', 'remove-submitted', 'done-submitted'],
    props: {
        tasks: {
            type: Array,
            required: true
        }
    },
    methods: {
    }
}
</script>

<style>
    .task-container {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        background-color: rgb(255, 255, 255);
        width: 70%;
        margin: 10px;
        text-align:initial;
        border-radius: 5px;
        box-shadow: 3px 2px 7px rgb(119, 112, 112);
        transition: transform 60ms ease;
    }

    .p-task {
        font-family: 'Poppins', sans-serif;
        font-weight: 600;
        margin: 5px 0px;
        color: #19232e;
    }

    .task-buttons {
        display: flex;
        flex-direction: row;
        align-items: center;
    }

    .done-button {
        margin-left: 10px;
        color: green;

    }


</style>
