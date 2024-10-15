<template>
<div class="weather-panel">
  <h1>Today's Weather</h1>
  <img :src="getIcon(weather.iconPhrase)" alt="Weather Icon" class="weather-icon" />
  <p class="descriptive-text">{{ weather.iconPhrase }}</p>
  <p class="descriptive-text">Average Temperature:</p>
  <h1 class="main-number">{{ weather.avgTemperature }}</h1>
  <p class="descriptive-text">Precipitation Probability:</p>
  <h1 class="secondary-number"> {{ weather.avgPrecipitation }}%</h1>

</div>
</template>

<script>
export default {

props: {
  weather:{
    type: Object,
    required: true
  }
},

methods: {
getIcon(iconPhrase) {
   switch (iconPhrase) {
      case 'Sunny':
      case 'Mostly Sunny':
          return require('@/assets/sunny.svg');
      case 'Partly Sunny':
      case 'Intermittent Clouds':
      case 'Hazy Sunshine':
        return require('@/assets/partly-cloudy.svg')
      case 'Mostly Cloudy':
      case 'Cloudy':
      case 'Dreary (Overcast)':
      case 'Fog':
        return require('@/assets/mostly-cloudy.svg');
      case 'Showers':
      case 'Mostly Cloudy w/ Showers':
      case 'Rain':
      case 'Freezing Rain':
        return require('@/assets/rainy.svg');
      case 'Partly Cloudy w/ Showers':
      case 'Partly Sunny w/ Showers': 
        return require('@/assets/sunny-rainy.svg');
      case 'T-Storms':
      case 'Mostly Cloudy w/ T-Storms':
        return require('@/assets/storm.svg');
      case 'Partly Sunny w/ T-Storms': 
        return require('@/assets/sunny-storm.svg');
      case 'Flurries':
      case 'Mostly Cloudy w/ Flurries':
      case 'Partly Sunny w/ Flurries':
      case 'Snow':
      case 'Mostly Cloudy w/ Snow':
      case 'Ice':
      case 'Sleet':
      case 'Rain and Snow':
        return require('@/assets/snow.svg');
      default:
        return require('@/assets/sunny-storm-wind.svg');  // Fallback for unknown phrases
      }
    },

}
};
</script>

<style scoped>
.weather-icon{

width: 90%;
height: 90%;
margin-top: -15%;
margin-bottom: -15%;
}
.weather-panel{
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;

}
h1 {
    text-align: center;
}
</style>