<template>
  <div>
    <div v-if="tasks.length">
      <TaskItem
          v-for="task in tasks"
          :key="task.id"
          :task="task"
          @delete-task="$emit('delete-task', task.id)" />
    </div>
    <p v-else>No hay tareas.</p>
  </div>
</template>

<script>
import TaskItem from './TaskItem.vue';

export default {
  props: {
    tasks: {
      type: Array,
      required: true,
    },
  },
  components: {
    TaskItem,
  },
};
</script>