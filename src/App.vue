<script setup>
import { reactive } from 'vue';


  const estado = reactive({
    filtro: 'todas',
    tarefaTemp: '',
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

  const getPendingTasks = ()=>{
    return estado.tarefas.filter( tarefa => !tarefa.finalizada )
  }

  const getTasksDone = ()=> {
    return estado.tarefas.filter( tarefa => tarefa.finalizada )
  }

  const getFilteredTasks = () => {
    const {filtro} = estado

    switch(filtro) {
      case 'pendentes':
        return ge.tPendingTasks()
      case 'finalizadas':
        return getTasksDone()
      default:
        return estado.tarefas
    }
  }

  const cadastraTarefa = () => {
    const tarefaNova = {
      titulo: estado.tarefaTemp,
      finalizada: false
    }
    estado.tarefas.push(tarefaNova)
    estado.tarefaTemp = ''
  }

</script>

<template>
  <div class="container">
    <header class="p-5 mt-4 mb-4 rounded-3 bg-light">
    <h1>Minhas tarefas</h1>
    <p>
      Você possui {{ getPendingTasks().length }} tarefas pendentes
    </p>
  </header>
  <form @submit.prevent="cadastraTarefa">
      <div class="row">
          <div class="col">
          <input :value="estado.tarefaTemp" @change="evento => estado.tarefaTemp = evento.target.value" type="text" placeholder="Digite aqui sua tarefa" class="form-control">
        </div>
        <div class="col-md-2">
          <button class="btn btn-primary" type="submit">Cadastrar</button>
        </div>
        <div class="col-md-2">
          <select @change="evento => estado.filtro = evento.target.value" class="form-control">
            <option value="todas">Todas tarefas</option>
            <option value="pendentes">Pendentes</option>
            <option value="finalizadas">Finalizadas</option>
          </select>
        </div>
      </div>
    </form>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in getFilteredTasks()">
        <input @change="evento => tarefa.finalizada = evento.target.checked " :checked="tarefa.finalizada" :id="tarefa.titulo" type="checkbox">
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
