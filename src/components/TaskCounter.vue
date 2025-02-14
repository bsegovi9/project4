<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  total: Number,
  completed: Number
});
</script>

<template>
  <div>
    <h4>Total Tasks: {{ total }}</h4>
    <h4>Completed: {{ completed }}</h4>
  </div>
</template>
