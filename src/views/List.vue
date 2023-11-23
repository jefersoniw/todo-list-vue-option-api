<template>
  <div class="container mt-2">
    <div class="mt-2" :key="index" v-for="(task, index) in tasks">
      <b-card :title="task.subject">
        <b-card-text>{{ task.description }}</b-card-text>

        <b-button variant="outline-primary" @click="editTask(index)">Editar</b-button>
        &nbsp
        <b-button variant="outline-danger" @click="deleteTask(index)">Apagar</b-button>
      </b-card>
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
    }
  }
}
</script>
