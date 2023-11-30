<script setup>
    const {data:login} = await useFetch("http://localhost:8000/usuarios");
    let selectedEmail = null;
</script>

<template>
    <div>
        <h1>My home Page!</h1>
        <img alt="Logo Senai" src="../image/senai.png">
        <br>
        <br>
        <select v-model="selectedEmail"> <option>Selecione</option>
            <option v-for="(users, index) in login.data" :key="index" :value="users.email">{{ users.email }}</option>
        </select>              
    </div>
</template>