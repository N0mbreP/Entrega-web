<template>
  <form class="input-section" @submit.prevent="onSubmit">
    <input
      type="text"
      v-model="taskText"
      @keyup.enter="onSubmit"
      placeholder="Escriu una nova tasca"
    />
    <button type="submit">Afegir</button>
  </form>
</template>

<script setup>
import { ref } from 'vue';
const emit = defineEmits(['add-task']);
const taskText = ref('');

function onSubmit() {
  if (taskText.value.trim() === '') return;
  emit('add-task', taskText.value);
  taskText.value = '';
}
</script>

<style scoped>
.input-section {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}
.input-section input[type="text"] {
  flex-grow: 1;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1em;
}
.input-section button {
  padding: 10px 15px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1em;
}
.input-section button:hover {
  background-color: #45a049;
}
</style>
