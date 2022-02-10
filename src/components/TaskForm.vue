<template>
    <form @submit.prevent="onSubmit">
        <label for="taskText">Add a new to-do</label>
        <textarea id="taskText" v-model="taskText"></textarea>
        <input class="button" type="submit" value="Add">  
    </form>
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

</style>
