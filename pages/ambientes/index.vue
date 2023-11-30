<script setup>
    const {data:ambientes} = await useFetch("http://localhost:8000/ambientes");
</script>

<template>
    <div>
      <h1>Ambientes</h1>
      <div v-for="(local, index) in ambientes.data" :key="index">
          <p>{{ local.nome }}</p>
      </div>
      <br>
      <h2>Adicionar um novo Ambiente</h2>
      <form @submit.prevent="enviarCadastro">
      <label for="nome">Nome:</label>
      <input type="text" id="nome" v-model="novoAmbiente.Nome" required>
  
      <button type="submit">Enviar</button>
    </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        novoAmbiente: {
          Nome: ''
        }
      };
    },
    methods: {
      enviarCadastro() {
        axios.post('https://localhost:8000/ambientes/', this.novoAmbiente)
          .then(response => {
            console.log('Cadastro enviado com sucesso!', response.data);
          })
          .catch(error => {
            console.error('Erro ao enviar cadastro:', error);
          });
      }
    }
  };
  </script>
  

  