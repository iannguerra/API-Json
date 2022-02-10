<template>
  <div class="main-container">
    <h1>LISTA DE USUARIOS</h1>
    <input type="text" v-model="Id" @keyup.enter="getUsers">
    <input type="text" v-model="firstName" @keyup.enter="getfirstName" placeholder="firstName">
    <input type="text" v-model="lastName" @keyup.enter="getlastName" placeholder="lastName">
    <input type="text" v-model="email" @keyup.enter="getemail" placeholder="email">
    <input type="text" v-model="adress" @keyup.enter="getadress" placeholder="adress">
    <ul>
      <li v-for="user of users" :key="user.id">
        {{user.id}} by {{user.firstName}}
      </li>
    </ul>

  </div>
</template>

<script>

</script>