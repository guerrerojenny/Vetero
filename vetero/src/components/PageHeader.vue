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
        <img class="profile-pic" src="https://via.placeholder.com/50" alt="User Profile">
      </div>
    </header>
  </template>
  
  <script>
 
  export default {
    data() {
    return {
      selectedTab: 'Outfit of the day'
    };
  },
  methods: {
    selectContent(tab) {
      this.selectedTab = tab;
    }
  },
    name: 'PageHeader'
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
  color: #333;
}

.menu p:hover {
  background-color: #e0e0e0;
}

.menu p.active {
  font-weight: bold;
  border-bottom: 2px solid #000;
}
  </style>
  