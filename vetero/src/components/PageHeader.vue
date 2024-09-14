<template>
    <header class="header">
      <div class="heading">Vetero</div>
      <div class="user-profile">
        <img class="profile-pic" src="https://via.placeholder.com/50" alt="User Profile">
      </div>
    </header>
  </template>
  
  <script>
  export default {
    name: 'Header'
  };
  </script>
  
  <style scoped>
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    background-color: #f0f0f0;
  }
  
  .heading {
    font-size: 24px;
    font-weight: bold;
  }
  
  .user-profile .profile-pic {
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }
  </style>
  