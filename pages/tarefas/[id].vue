<script setup>
    const route = useRoute();
    const {data} = await useFetch(`http://localhost:8000/tarefas/${route.params.id}`);
</script>

<template>
    <h1>oi</h1>
</template>