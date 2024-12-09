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

<style scoped>
/* Estilo general */
.container {
  font-family: 'Arial', sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.app-title {
  text-align: center;
  color: #4CAF50;
  font-size: 2rem;
}

.card {
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 20px;
}

button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 10px 15px;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 10px 0;
  padding: 10px;
  background-color: #f9f9f9;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.completed {
  text-decoration: line-through;
  color: gray;
}
</style>