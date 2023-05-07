<script setup>
    const props = defineProps(['pendingTasks'])
</script>

<template>
    <header class="p-5 mt-4 mb-4 rounded-3 bg-light">
        <h1>Minhas tarefas</h1>
        <p>
            Você possui {{ props.pendingTasks }} tarefas pendentes
        </p>
    </header>
</template>