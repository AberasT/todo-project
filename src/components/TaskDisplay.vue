<template>
    <task-list @edit-submitted="updateInput" @remove-submitted="removeTask" @done-submitted="setDone" :tasks="tasks"></task-list>
    <div>
        <form @submit.prevent="onSubmit">
            <textarea id="taskText" v-model="inputText"></textarea>
            <input class="button" type="submit" :value="buttonText">
        </form>
    </div>
    <h2>Done</h2>
    <done-task-list @remove-done-submitted="removeDoneTask" :doneTasks="doneTasks"></done-task-list>

</template>

<script>
import TaskList from "./TaskList.vue";
import DoneTaskList from "./DoneTaskList.vue";

export default {
    name: 'TaskDisplay',
    data() {
        return {
        tasks: [],
        doneTasks: [],
        inputText: '',
        buttonText: 'Add To-Do',
        auxIndex: null
        }
    },
    components: {
        DoneTaskList,
        TaskList
    },
    methods: {
        updateInput(index,task) {
            this.buttonText = 'Edit To-Do';
            this.inputText = task.text;
            this.auxIndex = index;
        },
        onSubmit() {
            if (this.inputText !== '') {
                if (this.buttonText == 'Add To-Do') {
                    this.addTask(this.inputText);
                } else {
                    this.editTask(this.inputText)
                }
            }
        },
        addTask(taskText) {
            let addedTask = {
                text: taskText,
                checked: false
            }
            this.tasks.push(addedTask);
            this.inputText = '';
        },
        editTask(editedTask) {
            let replaceTask = {
                text: editedTask,
                checked: false
            }
            this.tasks[this.auxIndex] = replaceTask;
            this.inputText = '';
            this.buttonText = 'Add To-Do'
        },
        removeTask(index) {
            this.tasks.splice(index);
        },
        removeDoneTask(index) {
            this.doneTasks.splice(index);
        },
        setDone(index) {
            this.doneTasks.push(this.tasks[index]);
            this.tasks.splice(index);
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
        border: none;
        background-color: rgb(22, 22, 22,0);
        margin: 5px;
        font-family: 'Poppins', sans-serif;
        color: rgb(22, 22, 22);
        text-shadow: 1px 1px 1px grey;
        font-weight: 600;
        cursor: pointer;
    }

    .button:hover {
        transform: scale(1.1);
    }
</style>
