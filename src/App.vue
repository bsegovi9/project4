<script setup>
import { ref, computed, onMounted } from 'vue';
import Header from './components/Header.vue';
import TaskList from './components/TaskList.vue';
import AddTask from './components/AddTask.vue';
import TaskCounter from './components/TaskCounter.vue';

const tasks = ref([]);

const totalTasks = computed(() => tasks.value.length);
const completedTasks = computed(() => tasks.value.filter(task => task.completed).length);

const addTask = (taskText) => {
  tasks.value.push({
    id: generateID(),
    text: taskText,
    completed: false
  });
  saveToLocalStorage();
};

const toggleTask = (id) => {
  const task = tasks.value.find(task => task.id === id);
  if (task) task.completed = !task.completed;
  saveToLocalStorage();
};

const deleteTask = (id) => {
  tasks.value = tasks.value.filter(task => task.id !== id);
  saveToLocalStorage();
};

const generateID = () => Math.floor(Math.random() * 1000000);

const saveToLocalStorage = () => {
  localStorage.setItem('tasks', JSON.stringify(tasks.value));
};

onMounted(() => {
  const savedTasks = JSON.parse(localStorage.getItem('tasks'));
  if (savedTasks) tasks.value = savedTasks;
});
</script>

<template>
  <Header />
  <div class="container">
    <TaskCounter :total="totalTasks" :completed="completedTasks" />
    <AddTask @taskAdded="addTask" />
    <TaskList :tasks="tasks" @taskToggled="toggleTask" @taskDeleted="deleteTask" />
  </div>
</template>

<style>
.container {
  max-width: 400px;
  margin: auto;
  text-align: center;
  font-family: Arial, sans-serif;
}
</style>
