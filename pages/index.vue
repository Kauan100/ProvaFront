<script setup>
    const {data:login} = await useFetch("http://localhost:8000/usuarios");
    import {ref} from 'vue';
    const selectedEmail = ref('')
</script>

<template>
    <div>
        <h1>My home Page!</h1>
        <img alt="Logo Senai" src="../image/senai.png">
        <br>
        <br>
        <select v-model="selectedEmail">
            <option v-for="(users, index) in login.data" :key="index" :value="users.email">{{ users.email }}</option>
        </select> 
        <NuxtLink to="home"><button v-if="selectedEmail !=''"></button></NuxtLink>             
    </div>
</template>

<!-- <script setup>
  const { data: login } = await useFetch("http://localhost:8000/usuarios");
  let selectedEmail = null;
  let isEmailSelected = false;

  function checkEmailSelection() {
    isEmailSelected = selectedEmail !== null && selectedEmail !== "Selecione";
  }

  // Chama a função para verificar se o e-mail foi selecionado sempre que houver mudanças em selectedEmail
  watch(() => selectedEmail, checkEmailSelection);
</script>

<template>
  <div>
    <h1>Minha Página Inicial!</h1>
    <img alt="Logo Senai" src="../image/senai.png">
    <br>
    <br>
    <select v-model="selectedEmail">
      <option disabled value="Selecione">Selecione</option>
      <option v-for="(user, index) in login.data" :key="index" :value="user.email">{{ user.email }}</option>
    </select>
    <button v-if="isEmailSelected" @click="loginUser">Login</button>
  </div>
</template> -->
