<template>
    <header class="header">
      <div class="heading">Vetero</div>
      <div class="menu-container">
        <div class="menu">
          <p
            :class="{ active: selectedTab === 'Outfit of the day' }"
            @click="selectContent('Outfit of the day')">Outfit of the day</p>
          <p 
            :class="{ active: selectedTab === 'Wardrobe' }"
            @click="selectContent('Wardrobe')">Wardrobe</p>
          <p 
            :class="{ active: selectedTab === 'Feedback' }"
            @click="selectContent('Feedback')">Feedback</p>
        </div>
      </div>
      <div class="user-profile">
        <img class="profile-pic" @click="openProfileOptions" src="https://via.placeholder.com/50" alt="User Profile">
      </div>
    </header>
    <div v-if = "visibleMenu" class="profileMenu">
      <p class="menuOption" @click="switchToAccountPage">Account</p>
      <button class="logOut" @click="logOut">Log Out</button>
    </div>
  </template>
  
  <script>
 
  export default {
    data(){
      return{
        visibleMenu: false
      }
    },
    methods: {
      selectContent(content) {
        this.$emit('tab-selected', content);
      },
      openProfileOptions(){
        this.visibleMenu = !this.visibleMenu;
      },
      switchToAccountPage(){
        console.log("Switch to account page!");
      },
      logOut(){
        this.$emit('logOut', false);
      }
    }
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

  .menu-container {
  display: flex;
  justify-content: center;
  width: 100%;
}

.menu {
  width: 66.66%;
  display: flex;
  justify-content: space-around;
  background-color: #f0f0f0;
  padding: 10px;
}

.menu p {
  cursor: pointer;
  margin: 0;
  padding: 10px 20px;
  color: gray;
}

.menu p:hover {
  color:#333;
  text-decoration: underline;
}

.menu p:active{
  color:#333;
  text-decoration: underline;
}

.primary{
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 5px 10px;
  cursor: pointer;
}

.profileMenu{
  position: fixed;
  right: 0;
  padding: 2%;
  z-index: 10;
  display: flex;
  flex-direction: column;
  height: 15%;
  width: 10%;
  background-color: azure;
}

.logOut{
  margin-top: 20%;
  margin-bottom: 10%;
  background-color:#ff5f62cb;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.logOut:hover{
  background-color:#ff3c3f;
}

.menuOption{
  color: gray;
}

.menuOption:hover{
  color:#333;
  text-decoration: underline;
}

  </style>
  