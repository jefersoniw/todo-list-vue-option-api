<template>
  <div class="container mt-2">
    <div v-if="tasks == ''">
      <div>
        <div class="verificacao">Sem Tarefas!</div>
      </div>
    </div>
    <div class="mt-2" :key="index" v-for="(task, index) in tasks">
      <div>
        <b-card :title="task.subject">
          <b-card-text>{{ task.description }}</b-card-text>

          <b-button variant="outline-primary" @click="editTask(index)">Editar</b-button>
          &nbsp
          <b-button variant="outline-danger" @click="deleteTask(index)">Apagar</b-button>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'List',
  data() {
    return {
      tasks: []
    }
  },
  created() {
    this.tasks = (localStorage.getItem('tasks')) ? JSON.parse(localStorage.getItem('tasks')) : []
  },
  methods: {
    editTask(idx) {
      this.$router.push({ name: 'form', params: { idx } });
    },
    deleteTask(idx) {
      let tasks = JSON.parse(localStorage.getItem('tasks'));
      tasks.splice(idx, 1);

      localStorage.removeItem('tasks');
      localStorage.setItem('tasks', JSON.stringify(tasks));

      location.reload();
    }
  }
}
</script>
<style>
.verificacao {
  font-weight: bold;
  font-size: 1.5rem;
  text-align: center;
}
</style>
