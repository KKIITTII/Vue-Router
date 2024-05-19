<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link :to="{ name: 'about' }">About</router-link> |
    <router-link :to="{ name: 'jobs' }">Jobs</router-link>
    <br>
  </nav>

  <button @click="redirect">Redirect</button>
  <button @click="back">Go Back</button>
  <button @click="forward">Go Forward</button>


  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  border-radius: 4px;
  padding: 10px;
}

nav a.router-link-exact-active {
  color: #42b983;
  background: crimson;
}
</style>


<script setup>

import { useRouter } from 'vue-router';
const router = useRouter()
const back = () => {
    router.go(-1)
}

const redirect = () => {
    router.push({ name: 'home'})
}

const forward = () => {
    router.go(1)
}

</script>