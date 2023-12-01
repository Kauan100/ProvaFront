<script setup>
    const {data:ambientes} = await useFetch("http://localhost:8000/ambientes");
    import { ref } from 'vue';
    const host = ref('')
    const savedra = async() => {
      await useFetch('http://localhost:8000/ambientes/',{
        method:"POST",
        body:[{
          'nome':host
        }]
      })
    }
</script>

<template>
    <div>
      <Menu></Menu>
      <h1>Ambientes</h1>
      <div v-for="(local, index) in ambientes.data" :key="index">
          <p>{{ local.nome }}</p>
      </div>
      <br>
      <h2>Adicionar um novo Ambiente</h2>
      <label for="nome">Nome:</label>
      <input type="text" id="nome" v-model="host" required>
  
      <button @click=savedra type="submit">Enviar</button>
    </div>
  </template>
  
  