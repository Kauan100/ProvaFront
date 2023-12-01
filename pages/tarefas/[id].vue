<script setup>
    const route = useRoute();
    const {data} = await useFetch(`http://localhost:8000/tarefas/${route.params.id}`);
    const {data:taskUser} = await useFetch(`http://localhost:8000/tarefasUsuarios?tarefa=${route.params.id}`);
</script>

<template>
    <div>
        <Menu></Menu>
        <h1>Dados da Tarefa Completa</h1>
        <div>{{ data.data.nome }}</div>
        <div>{{ data.data.idStatusFK.nome }}</div>
        <div>{{ data.data.idAmbienteFK.nome }}</div>
        <div>{{ data.data.dataInicio }}</div>
        <div>{{ data.data.dataFim }}</div>
        <div>{{ data.data.descricao }}</div>
        <br>
        <h2>Solicitante</h2>
        <div>{{ data.data.idSolicitanteFK.nome }}</div>
        <img :src="`${data.data.idSolicitanteFK.image}`" alt="">
        <h2>Responsáveis</h2>
        <div>{{ taskUser.data[0].idUsuarioFK.nome }}</div>
        <img :src="`${taskUser.data[0].idUsuarioFK.image}`">

    </div>
</template>