<script setup>
import { reactive } from "vue";
import Cabecalho from "./components/Cabecalho.vue";
import Formulario from "./components/Formulario.vue";
import ListaDeTarefas from "./components/ListaDeTarefas.vue";

const estado = reactive({
  filtro: "todas",
  tarefaTemp: "",
  tarefas: [
    {
      titulo: "Pagar cartão Inter",
      finalizada: false,
    },
    {
      titulo: "Estudar faculdade",
      finalizada: false,
    },
    {
      titulo: "Estudar VueJS",
      finalizada: true,
    },
  ],
});

const getPendingTasks = () => {
  return estado.tarefas.filter((tarefa) => !tarefa.finalizada);
};

const getTasksDone = () => {
  return estado.tarefas.filter((tarefa) => tarefa.finalizada);
};

const getFilteredTasks = () => {
  const { filtro } = estado;

  switch (filtro) {
    case "pendentes":
      return getPendingTasks();
    case "finalizadas":
      return getTasksDone();
    default:
      return estado.tarefas;
  }
};

const cadastraTarefa = () => {
  const tarefaNova = {
    titulo: estado.tarefaTemp,
    finalizada: false,
  };
  estado.tarefas.push(tarefaNova);
  estado.tarefaTemp = "";
};
</script>

<template>
  <div class="container">
    <Cabecalho :pending-tasks="getPendingTasks().length" />
    <Formulario :trocar-filtro="evento => estado.filtro = evento.target.value" :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" :cadastra-tarefa="cadastraTarefa"/>
    <ListaDeTarefas :tarefas="getFilteredTasks()"/>
  </div>
</template>


