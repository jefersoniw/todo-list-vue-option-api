<template>
  <div class="container mt-2">
    <b-form>
      <b-form-group label="Titulo" label-for="subject">
        <b-form-input id="subject" v-model="form.subject" type="text" placeholder="Ex: Lavar carro" required
          auto-complete="off"></b-form-input>
      </b-form-group>

      <b-form-group label="Descrição" label-for="description" class="mt-3">
        <b-form-textarea id="description" v-model="form.description" type="text"
          placeholder="Ex: Preciso levar o carro para lavar hoje à tarde" required auto-complete="off"></b-form-textarea>
      </b-form-group>

      <b-button class="mt-3" type="submit" variant="outline-success" @click="saveTask">Salvar</b-button>
    </b-form>
  </div>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return {
      form: {
        subject: null,
        description: null
      },
      methodSave: 'new',
    }
  },
  methods: {
    saveTask(e) {
      e.preventDefault();

      if (this.methodSave === 'update') {
        let tasks = JSON.parse(localStorage.getItem('tasks'));
        tasks[this.$route.params.idx] = this.form
        localStorage.setItem('tasks', JSON.stringify(tasks));
        this.$router.push({ name: 'list' });

      } else {
        let tasks = (localStorage.getItem('tasks')) ? JSON.parse(localStorage.getItem('tasks')) : [];
        tasks.push(this.form);
        localStorage.setItem('tasks', JSON.stringify(tasks));
        this.$router.push({ name: 'list' });

      }



    }
  },
  created() {
    //PEGANDO O INDICE DA TAREFA DO LOCAL STORAGE E EXIBINDO NO FORM
    if (this.$route.params.idx === 0 || this.$route.params.idx !== undefined) {
      this.methodSave = 'update';
      let tasks = JSON.parse(localStorage.getItem('tasks'));
      this.form = tasks[this.$route.params.idx];
    }
  }

}
</script>
