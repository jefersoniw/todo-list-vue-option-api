<template>
  <div id="app">
    <NavBar />
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view />
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue';

export default {
  name: 'App',
  data() {
    return {

    }
  },
  components: {
    NavBar
  }
}
</script>

<style></style>
