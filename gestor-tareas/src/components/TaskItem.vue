<template>
  <div class="task-item">
    <span :class="{ completed: task.completed }">{{ task.name }}</span>
    <button @click="$emit('delete-task', task.id)">Eliminar</button>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.task-item {
  display: flex;
  justify-content: space-between;
  margin: 5px 0;
}
.completed {
  text-decoration: line-through;
  color: gray;
}
</style>