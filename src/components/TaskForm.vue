<template>
    <form @submit.prevent="onSubmit">
        <label>Add a new to-do</label>
        <input type="text" id="newTask" v-model="newTask">
        <input type="submit" value="Add">  
    </form>
</template>

<script>

export default {
    name: 'TaskForm',
    data() {
        return {
            newTask: ''
        }
    },
    methods: {
        onSubmit() {
            if (this.newTask !== '') {
                this.$emit('task-added',this.newTask);
                this.newTask = '';
            }
        }
    }
}
</script>

<style>

</style>
