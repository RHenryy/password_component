<template>
  <div id="app">
    <h1 class="mb-5">Password Project</h1>
    <PasswordForm msg="Password Form"/>
   

  </div>
</template>

<script>
import PasswordForm from './components/PasswordForm.vue'

export default {
  name: 'App',
  components: {
    PasswordForm
  }, 
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app h1 {
  font-size: 3rem;
}
#app h2 {
  font-size: 2rem;
}
</style>
