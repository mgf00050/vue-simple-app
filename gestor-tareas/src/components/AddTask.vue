<template>
  <form @submit.prevent="submitTask">
    <input type="text" v-model="taskName" placeholder="Nueva tarea" required />
    <button type="submit">Agregar</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      taskName: '',
    };
  },
  methods: {
    submitTask() {
      if (this.taskName.trim()) {
        this.$emit('add-task', { id: Date.now(), name: this.taskName, completed: false });
        this.taskName = ''; // Limpia el input
      }
    },
  },
};
</script>

<style scoped>
/* Estilos para el formulario */
form {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}
</style>