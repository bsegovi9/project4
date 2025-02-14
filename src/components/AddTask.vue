<script setup>
import { ref, defineEmits } from 'vue';

const taskText = ref('');
const emit = defineEmits(['taskAdded']);

const addTask = () => {
  if (taskText.value.trim() !== '') {
    emit('taskAdded', taskText.value);
    taskText.value = '';
  }
};
</script>

<template>
  <form @submit.prevent="addTask">
    <input type="text" v-model="taskText" placeholder="Enter a task..." />
    <button>Add Task</button>
  </form>
</template>

<style>
input {
  width: 80%;
  padding: 5px;
  margin-right: 5px;
}
button {
  padding: 5px;
}
</style>

