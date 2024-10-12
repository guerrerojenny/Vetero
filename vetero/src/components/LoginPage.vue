<template>
    <div class="login-page">
      <h2>Login</h2>
      <form @submit.prevent="login">
        <input v-model="email" placeholder="Email" required />
        <input v-model="password" type="password" placeholder="Password" required />
        <button type="submit">Login</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        email: '',
        password: ''
      };
    },
    methods: {
      login() {
        // add your login logic (e.g., API call)
        this.$emit('login-success');
      }
    }
  };
  </script>
  
  <style scoped>



</style>
  