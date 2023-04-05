<template>
  <AddTask v-show="showAddTask" @add-task="addTask" />
  <Tasks
    @toggle-reminder="toggleReminder"
    @delete-task="deleteTask"
    :tasks="tasks"
  />
</template>

<script>
import Tasks from '../components/Tasks.vue';
import AddTask from '../components/AddTask.vue';

export default {
  name: 'Home',
  components: { Tasks, AddTask },
  props: {
    showAddTask: Boolean,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    deleteTask({ text, id }) {
      if (confirm(`Você quer deletar a task: ${text}`)) {
        this.tasks = this.tasks.filter((task) => {
          return task.id !== id;
        });
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Consulta médica',
        day: '14 de Abril às 14:30',
        reminder: true,
      },
      {
        id: 2,
        text: 'Daily',
        day: '10 de Abril às 09:30',
        reminder: true,
      },
      {
        id: 3,
        text: 'Comprar comida',
        day: '11 de Abril às 19:00',
        reminder: false,
      },
    ];
  },
};
</script>
