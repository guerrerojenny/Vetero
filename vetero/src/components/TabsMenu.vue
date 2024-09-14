<template>
    <div class="menu">
      <ul>
        <li @click="selectContent('Outfit of the day')">Outfit of the day</li>
        <li @click="selectContent('Wardrobe')">Wardrobe</li>
        <li @click="selectContent('Feedback')">Feedback</li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    methods: {
      selectContent(content) {
        this.$emit('menu-selected', content);
      }
    }
  };
  </script>
  
  <style scoped>
  .menu ul {
    list-style: none;
    padding: 0;
  }
  
  .menu li {
    cursor: pointer;
    padding: 10px 0;
  }
  
  .menu li:hover {
    text-decoration: underline;
  }
  </style>
  