<template>
  <ul class="task-list">
    <TaskItem
      v-for="task in tasks"
      :key="task.id"
      :task="task"
      @toggle-task="$emit('toggle-task', $event)"
      @delete-task="$emit('delete-task', $event)"
    />
  </ul>
</template>

<script setup>
import TaskItem from './TaskItem.vue';
const props = defineProps({
  tasks: {
    type: Array,
    required: true
  }
});
const emit = defineEmits(['toggle-task', 'delete-task']);
</script>

<style scoped>
.task-list {
  list-style: none;
  padding: 0;
}
</style>
