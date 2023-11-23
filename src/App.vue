<template>
  <div id="app">
    <NavBar />
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
