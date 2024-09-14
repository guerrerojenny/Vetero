<template>
    <div class="weather-panel">
      <h1>Today's Weather</h1>
      <!--Icon
      // <img alt="Weather Icon" src="getWeatherIcon(iconPhrase)">
      // Avg temp
      // low | high
      // Chance of precipitation
      // By hours?-->
    </div>
  </template>
  
  <script>
  export default {
    /*
    props: {
      iconPhrase: {
        type: String,
        required: true
      }
    },
    */
    methods: {
      selectContent(content) {
        this.$emit('menu-selected', content);
      }/*,
      getWeatherIcon(phrase) {
        switch (phrase.toLowerCase()) {
          case 'sunny':
            return require('@/assets/sunny.svg');
          case 'cloudy':
            return require('@/assets/cloudy.svg');
          case 'rainy':
            return require('@/assets/rainy.svg');
          default:
            return require('@/assets/default-icon.svg');  // Fallback for unknown phrases
        }
      }
        */
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
  