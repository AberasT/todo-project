<template>
    <div>
        <form @submit.prevent="onSubmit">
            <textarea placeholder="Write here!" id="taskText" v-model="inputText"></textarea>
            <input class="button add-button" type="submit" :value="buttonText">
        </form>
    </div>
    <task-list @edit-submitted="updateInput" @remove-submitted="removeTask" @done-submitted="setDone" :tasks="tasks"></task-list>
    
    <p v-if="this.doneTasks.length">Done</p>
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
            if (this.buttonText == 'Add To-Do') {
                index == 0 ? this.tasks.shift(index) : this.tasks.splice(index,1);
            }
        },
        removeDoneTask(index) {
            if (this.buttonText == 'Add To-Do') {
                index == 0 ? this.doneTasks.shift(index) : this.doneTasks.splice(index,1); 
            } 
        },
        setDone(index) {
            this.doneTasks.push(this.tasks[index]);
            this.removeTask(index);
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
        font-family: 'Poppins', sans-serif;
        font-size: medium;
    }
    .button {
        border: none;
        background-color: rgb(22, 22, 22,0);
        font-family: 'Poppins', sans-serif;
        font-weight: 600;
        cursor: pointer;
        transition: transform 60ms ease;
    }

    .color-red {
        color: rgb(184, 3, 3);
    }

    .color-blue {
        color: rgb(39, 174, 236);
    }

    .add-button {
        font-size: large;
    }

    .button:hover {
        transform: scale(1.07);
    }
</style>
