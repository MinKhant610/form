<template>
  <SignUp/>
</template>

<script>

import SignUp from "./components/Sign-up.vue";

export default {
  name: 'App',
  components: {
    SignUp,
  }
}
</script>

<style>
/* Only App.vue can select index.html styel */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body{
  margin: 0;
  background: #eee;
}
</style>
