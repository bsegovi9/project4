<script setup>
import { ref } from 'vue';
import AddTask from './components/AddTask.vue';

const tasks = ref([]);

const handleTaskAdded = (task) => {
  tasks.value.push(task);
};
</script>

<template>
  <div class="container">
    <h2>Task List</h2>
    <AddTask @taskAdded="handleTaskAdded" />
    <ul>
      <li v-for="(task, index) in tasks" :key="index">{{ task }}</li>
    </ul>
  </div>
</template>

<style>
.container {
  text-align: center;
  margin-top: 20px;
}
ul {
  list-style: none;
  padding: 0;
}
li {
  padding: 5px;
  background: #eee;
  margin: 5px 0;
}
</style>
