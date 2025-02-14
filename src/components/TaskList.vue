<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  tasks: Array
});

const emit = defineEmits(['taskToggled', 'taskDeleted']);

const toggleTask = (id) => {
  emit('taskToggled', id);
};

const deleteTask = (id) => {
  emit('taskDeleted', id);
};
</script>

<template>
  <ul>
    <li v-for="task in tasks" :key="task.id">
      <input type="checkbox" :checked="task.completed" @change="toggleTask(task.id)" />
      <span :style="{ textDecoration: task.completed ? 'line-through' : 'none' }">
        {{ task.text }}
      </span>
      <button @click="deleteTask(task.id)">X</button>
    </li>
  </ul>
</template>

<style>
ul {
  list-style: none;
  padding: 0;
}
li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 5px 0;
}
button {
  background: red;
  color: white;
  border: none;
  padding: 5px;
  cursor: pointer;
}
</style>
