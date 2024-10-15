<template>
  <div class="app-container">
    <PageHeader v-if="isLoggedIn" @tab-selected="updateContent"/> <!--render header if isLoggedIn is true-->
    <LoginPage v-else @login-success="handleLogin" /> <!--render login page if isLoggedIn is false-->
    <div class="main-layout" v-if="isLoggedIn"><!--render what is inside main layout if isLoggedIn is true-->
      <div class="left-column" v-if="isLoggedIn"> 
        <div class="menu-container">
          <WeatherPanel :weather="weatherData"></WeatherPanel>
        </div>
        <div class="extra-space">
        </div>
      </div>
      <!--Outfit content: Wardrobe, Outfit of the Day, Feedback-->
      <div class="right-column">
        <component :is="currentComponent" />
      </div>
    </div>   
  </div>
</template>

<script>
import PageHeader from './components/PageHeader.vue';
import WeatherPanel from './components/WeatherPanel.vue';
import WardrobePanel from './components/WardrobePanel.vue';
import OutfitPanel from './components/OutfitPanel.vue';
import FeedbackPanel from './components/FeedbackPanel.vue';
import LoginPage from './components/LoginPage.vue'; 


export default {
  components: {
    PageHeader,
    WeatherPanel,
    WardrobePanel,
    FeedbackPanel,
    OutfitPanel,
    LoginPage
  },
  data() {
    return {
      selectedContent: 'Feedback',
      isLoggedIn: false, //isLoggedIn is set to false by default (can change this based on cookie?)
      weatherData: {
        iconPhrase: "Sunny",
        avgTemperature: "50",
        avgPrecipitation: "5"
      }
    };
  },
  computed: {
    currentComponent() {
      if (!this.isLoggedIn) return null;
      switch (this.selectedContent) {
        case 'Outfit of the day':
          return 'OutfitPanel';
        case 'Wardrobe':
          return 'WardrobePanel';
        case 'Feedback':
          return 'FeedbackPanel';
        default:
          return null;
      }
    }
  },
  methods: {
    updateContent(content) {
      this.selectedContent = content;
    },
    handleLogin() {
      this.isLoggedIn = true; // isLoggedIn is set to true as response to LoginPage emitting 'login-success'
    }
  }
};
</script>




<style scoped>
.app-container {
  font-family: Arial, sans-serif;
  padding: 0.5%;
}

.main-layout {
  display: flex;
  margin-top: 1.25%;
}

.left-column {
  flex: 1;
  padding-right: 10%;
  display: flex;
  flex-direction: column;
}

.menu-container {
  flex: 1;
  margin-bottom: 20px;
}

.extra-space {
  flex: 2;
}

.right-column {
  flex: 3;
  padding-left: 20px;
}

.main-layout > div {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 10px;
}

@media (min-width: 768px) {
  .left-column {
    flex: 1;
  }

  .right-column {
    flex: 3;
  }
}
</style>
