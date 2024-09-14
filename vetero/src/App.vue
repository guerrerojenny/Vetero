<template>
  <div class="app-container">
    <Header />
    <div class="main-layout">
      <div class="left-column">
        <div class="menu-container">
          <Menu @menu-selected="updateContent" />
        </div>
        <div class="extra-space">
          <!-- You can add other left column content here -->
        </div>
      </div>
      <div class="right-column">
        <Content :selectedContent="selectedContent" />
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/PageHeader.vue';
import Menu from './components/TabsMenu.vue';
import Content from './components/MainContent.vue';

export default {
  components: {
    Header,
    Menu,
    Content
  },
  data() {
    return {
      selectedContent: 'Outfit of the day'
    };
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
  padding: 0 5%;
}

.main-layout {
  display: flex;
  margin-top: 20px;
}

.left-column {
  flex: 1;
  padding-right: 20px;
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
