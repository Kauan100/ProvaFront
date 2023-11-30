<script setup>
    const {data:cargos} = await useFetch("http://localhost:8000/cargos");
</script>

<template>
    <div>
      <h1>Cargos</h1>
      <div v-for="(profissao, index) in cargos.data" :key="index">
          <p>{{ profissao.nome }}</p>
      </div>
    </div>
  </template>