<script setup>
import { reactive } from 'vue';


  const estado = reactive({
    tarefas: [
      {
        titulo: 'Pagar cartão Inter',
        finalizada: false
      },
      {
        titulo: 'Estudar faculdade',
        finalizada: false
      },
      {
        titulo: 'Estudar VueJS',
        finalizada: true
      }
    ]
  })

</script>

<template>
  <div class="container">
    <header class="p-5 mt-4 mb-4 rounded-3 bg-light">
    <h1>Minhas tarefas</h1>
    <p>
      Você possui 7 tarefas pendentes
    </p>
  </header>
  <form>
      <div class="row">
          <div class="col">
          <input type="text" placeholder="Digite aqui sua tarefa" class="form-control">
        </div>
        <div class="col-md-2">
          <button class="btn btn-primary" type="submit">Cadastrar</button>
        </div>
        <div class="col-md-2">
          <select class="form-control">
            <option value="Todas">Todas tarefas</option>
            <option value="Pendentes">Pendentes</option>
            <option value="Finalizadas">Finalizadas</option>
          </select>
        </div>
      </div>
    </form>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in estado.tarefas">
        <input :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
        <label :class="{ done: tarefa.finalizada }" class="ms-2" for="tarefa.titulo">
          {{ tarefa.titulo }}
        </label>
      </li>
    </ul>
  </div>
</template>

<style scoped>

  .done{
    text-decoration: line-through;
  }
</style>
