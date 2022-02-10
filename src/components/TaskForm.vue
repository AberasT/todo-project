<template>
    <div>
        <form @submit.prevent="onSubmit">
            <textarea id="taskText" v-model="taskText"></textarea>
            <input class="button" type="submit" value="Add To-Do">  
        </form>
    </div>
    
</template>

<script>

export default {
    name: 'TaskForm',
    data() {
        return {
            taskText: ''
        }
    },
    methods: {
        onSubmit() {
            if (this.taskText !== '') {
                this.$emit('task-added',this.taskText);
                this.taskText = '';
            }
        }
    }
}
</script>

<style>
    textarea {
        width: 100%;
        border: solid 2px black;
        resize: none;
        margin: 5px;
    }
    .button {
        border: solid 2px black;
        background-color: rgb(0, 0, 0);
        margin: 5px;
        font-family: 'Poppins', sans-serif;
        color: rgb(255, 255, 255);
        font-weight: 600;
        cursor: pointer;
    }
</style>
