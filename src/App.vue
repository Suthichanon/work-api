<script setup lang="ts">
import axios from "axios";
import { ref } from "vue";

const characters = ref();

axios
  .get("https://pokeapi.co/api/v2/pokemon/")
  .then(function (response) {
    characters.value = response.data.results;
    console.log(characters.value);
  })
  .catch(function (error) {
    console.log(error);
  });
</script>

<template>
  <nav class="navbar navbar-expand-sm nvabar-dark bg-dark" style="margin-left: 0rem">
    <RouterLink to="/" style="text-decoration: none; color: #fff">Home</RouterLink>
  </nav>
  <div class="container">
    <img style="height: 100px; margin-top: 0.5em" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/2560px-International_Pok%C3%A9mon_logo.svg.png" alt="Logo image" />
    <h1 class="page-header">Poekemon API</h1>
    <table>
      <thead>
        <th>Name</th>
      </thead>
      <tbody>
        <tr v-for="(character, index) in characters" :key="index">
          <td>{{ character.name }}</td>
        </tr>
      </tbody>
    </table>
  </div>
  <RouterView />
</template>

<style scoped>
.container img{
  border: 1px solid red;
  
}
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;
    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
