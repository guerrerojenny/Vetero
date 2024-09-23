<template>
  <div>
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
  }
};
</script>

<style scoped>
.menu {
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
