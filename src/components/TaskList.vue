<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  tasks: Array,
});

const emit = defineEmits(['taskDeleted']);

const deleteTask = (index) => {
  emit('taskDeleted', index);
};
</script>

<template>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      {{ task }}
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
</template>

<style>
ul {
  list-style: none;
  padding: 0;
}
li {
  padding: 5px;
  background: #eee;
  margin: 5px 0;
  display: flex;
  justify-content: space-between;
}
button {
  background: red;
  color: white;
  border: none;
  cursor: pointer;
}
</style>
