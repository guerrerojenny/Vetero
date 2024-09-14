<template>
    <div class="content">
      <h2>{{ selectedContent }}</h2>
      <p v-if="selectedContent === 'Outfit of the day'">Content for outfit of the day.</p>
      <p v-if="selectedContent === 'Wardrobe'">Content for wardrobe.</p>
      <p v-if="selectedContent === 'Feedback'">Content for feedback.</p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['selectedContent']
  };
  </script>
  
  <style scoped>
  .content {
    font-size: 18px;
  }
  </style>
  