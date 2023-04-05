<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input
        type="text"
        v-model="text"
        name="text"
        placeholder="Add Task"
        required
      />
    </div>
    <div class="form-control">
      <label>Dia e Hora</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Dia e Hora"
        required
      />
    </div>
    <div class="form-control form-control-check">
      <label>Lembrete</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Salve a Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: 'AddTask',
  data() {
    return {
      text: '',
      day: '',
      reminder: '',
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();

      const newTask = {
        id: Date.now(),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };

      this.$emit('add-task', newTask);

      this.text = '';
      this.day = '';
      this.reminder = false;
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>
