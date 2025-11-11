<template>
  <li :class="{ completed: task.completed }" class="task-item">
    <span class="task-text">{{ task.text }}</span>
    <button
      @click="emit('toggle-task', task.id)"
      :class="{ 'btn-mark': !task.completed, 'btn-unmark': task.completed }"
    >
      {{ task.completed ? 'Desmarcar' : 'Completar' }}
    </button>
    <button @click="emit('delete-task', task.id)" class="btn-delete">🗑️</button>
  </li>
</template>

<script setup>
const props = defineProps({
  task: {
    type: Object,
    required: true
  }
});
const emit = defineEmits(['toggle-task', 'delete-task']);
</script>

<style scoped>
.task-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 0;
  border-bottom: 1px dashed #eee;
}
.task-item.completed .task-text {
  text-decoration: line-through;
  color: #888;
}
.task-text {
  flex-grow: 1;
  font-size: 1.1em;
}
.btn-mark {
  background-color: #008CBA;
  color: white;
}
.btn-mark:hover {
  background-color: #007bb5;
}
.btn-unmark {
  background-color: #f44336;
  color: white;
}
.btn-unmark:hover {
  background-color: #da190b;
}
.btn-delete {
  background-color: #f44336;
  color: white;
  padding: 8px 10px;
}
.btn-delete:hover {
  background-color: #da190b;
}
</style>
