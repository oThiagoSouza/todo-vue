<script setup>
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
      <li class="list-group-item">
        <input type="checkbox">
        <label class="ms-2" for="">
          Pagar cartão Inter
        </label>
      </li>
    </ul>
  </div>
</template>

<style scoped>

</style>
