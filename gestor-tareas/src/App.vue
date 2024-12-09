<template>
  <div id="app">
    <h1>Gestor de Tareas</h1>
    <AddTask @add-task="addTask" />
    <TaskList :tasks="tasks" @delete-task="deleteTask" />
  </div>
</template>

<script>
import AddTask from './components/AddTask.vue';
import TaskList from './components/TaskList.vue';

export default {
  components: {
    AddTask,
    TaskList,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addTask(newTask) {
      this.tasks.push(newTask);
    },
    deleteTask(taskId) {
      this.tasks = this.tasks.filter(task => task.id !== taskId);
    },
    mounted() {
      const savedTasks = localStorage.getItem('tasks');
      if (savedTasks) {
        this.tasks = JSON.parse(savedTasks);
      }
    },
    watch: {
      tasks: {
        handler(newTasks) {
          localStorage.setItem('tasks', JSON.stringify(newTasks));
        },
        deep: true,
      },
    },
  },
};
</script>