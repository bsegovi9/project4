<script setup>
import { ref } from 'vue';
import AddTask from './components/AddTask.vue';
import TaskList from './components/TaskList.vue';

const tasks = ref([]);

const handleTaskAdded = (task) => {
  tasks.value.push(task);
};

const handleTaskDeleted = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <div class="container">
    <h2>Task List</h2>
    <AddTask @taskAdded="handleTaskAdded" />
    <TaskList :tasks="tasks" @taskDeleted="handleTaskDeleted" />
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
