<template>
  <h1>{{ titulo }}</h1>

  <input v-model="tarefa.descricao" type="text" placeholder="Descrição da tarefa">
  <button @click="adicionarTarefa">Adicionar</button>

  <table border="1">
    <thead>
      <th>Concluída</th>
      <th>Descrição</th>
    </thead>
    <tbody>
      <tr v-for="iterador in tarefas" :key="iterador.descricao" :class="{ riscado: iterador.concluida }">
        <td>
          <input type="checkbox" v-model="iterador.concluida">
        </td>
        <td>{{ iterador.descricao }}</td>
      </tr>
    </tbody>
  </table>

</template>

<script>
export default {
  data() {
    return {
      titulo: "Todolist Vite",
      tarefas: [],
      tarefa: {
        descricao: "",
        concluida: false
      }
    }
  },
  methods: {
    adicionarTarefa() {
      this.tarefas.push(Object.assign({}, this.tarefa))
    }
  }
}
</script>

<style>
  .riscado {
    text-decoration: line-through;
  }
</style>