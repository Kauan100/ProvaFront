<script setup>
    const {data:tarefas} = await useFetch("http://localhost:8000/tarefas");
</script>

<template>
  <div>
    <Menu></Menu>
    <h1>Tarefas</h1>
    <div v-for="(task, index) in tarefas.data" :key="index">
        <p>{{ task.idTarefaFK.idStatusFK.nome }}</p>
        <p>{{ task.idTarefaFK.idAmbienteFK.nome }}</p>
        <p>{{ task.idTarefaFK.prazo }}</p>
        <NuxtLink :to="`/tarefas/${task.idTarefaFK.id}`"><p>{{ task.idTarefaFK.nome }}</p></NuxtLink>
    </div>
  </div>
</template>
