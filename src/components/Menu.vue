<template>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/warehouses">Galpões</router-link> |
      <router-link to="/warehouses/new">Cadastrar Galpão</router-link>
    </nav>
</template>

<script>
  export default {
    name: 'Menu'
  }
</script>

<style>
  nav {
    padding: 30px;
  }

  nav a {
    font-weight: bold;
    color: #2c3e50;
  }

  nav a.router-link-exact-active {
    color: #42b983;
  }
</style>