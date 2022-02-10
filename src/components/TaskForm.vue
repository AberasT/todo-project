<template>
    <div @edit-submitted="updateInput">
        <form @submit.prevent="onSubmit">
            <textarea id="taskText" v-model="taskText"></textarea>
            <input class="button" type="submit" :value="buttonText">  
        </form>
    </div>
    
</template>

<script>

export default {
    name: 'TaskForm',
    data() {
        return {
            taskText: '',
            buttonText: 'Add To-Do'
        }
    },
    methods: {
        onSubmit() {
            if (this.taskText !== '') {
                if (this.buttonText == 'Add To-Do') {
                    this.$emit('task-added',this.taskText);
                    this.taskText = '';
                } else {
                    let editedTask = this.taskText;
                    this.$emit('task-edited',index,editedTask);
                    this.taskText = '';
                    this.buttonText = 'Add To-Do';
                }
            }
        },
        updateInput(task) {
            taskText = task.text;
            this.buttonText = 'Edit To-Do';
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
