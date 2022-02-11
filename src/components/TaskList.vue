<template>
    <div class="task-container" v-for="(task,index) in tasks" :key="index">
        <p class="p-task" >{{ task.text }}</p>
        <div class="task-buttons">
            <button 
                class="button" 
                @click='$emit("edit-submitted",index,task)'>
                Edit
            </button>
            <button 
                class="button" 
                @click="$emit('remove-submitted',index)">
                Remove
            </button>
            <input @click="$emit('done-submitted',index)" class="checkbox" type="checkbox" >
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
        background-color: rgb(246, 246, 246);
        width: 70%;
        margin: 10px;
        text-align:initial;
        border: rgb(200, 6, 6) solid;
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
