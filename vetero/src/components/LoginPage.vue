<template>
    <div class="login-page">
      <h2>Login</h2>
      <form @submit.prevent="login">
        <input v-model="email" placeholder="Email" required />
        <input v-model="password" type="password" placeholder="Password" required />
        
        <div>
          <button type="login">Login</button>
          <button type="sugnup">Sign Up</button>
        </div>
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
        // add login logic (e.g., API call)
        this.$emit('login-success');
      }
    }
  };
  </script>
  

  <style scoped>

  .login-page {
      display: flex;
      flex-direction: column;
      align-items: center;
  }
  .linput-fields{
      display: flex;
    gap: 10px;
    margin-bottom: 10px;
  }
  .buttons{
  display: flex;
    flex-direction: column;
    align-items: center;
    padding: 10px;
    background-color: #fff;
    cursor: pointer;
    border-radius: 5px;
  }
  </style>
  