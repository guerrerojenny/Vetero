<template>
  <div class="app-container">
    <PageHeader @menu-selected="updateContent"/>
    <div class="main-layout">
      <div class="left-column">
        <div class="menu-container">
          <WeatherPanel iconPhrase="Sunny"
           :avgTemperature="30" 
           :avgPrecipitation="5"/>
        </div>
        <div class="extra-space">
        </div>
      </div>
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


export default {
  components: {
    PageHeader,
    WeatherPanel,
    WardrobePanel,
    FeedbackPanel,
    OutfitPanel
  },
  data() {
    return {
      selectedContent: 'Outfit of the day'
    };
  },
  computed: {
    currentComponent() {
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
