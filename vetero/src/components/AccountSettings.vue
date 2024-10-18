<template>
    <div class="account-settings">
      <h2>Account Settings</h2>
      <div class="info">
        <p><strong>Email:</strong> {{ email }}</p>
        <p><strong>Location:</strong> {{ latitude }}, {{ longitude }}</p>
      </div>
  
      <div class="update-options">
        <div class="time-setting">
          <label for="daytimeStart">Daytime Start:</label>
          <input type="time" id="daytimeStart" v-model="daytimeStart" />
        </div>
        <div class="time-setting">
          <label for="daytimeEnd">Daytime End:</label>
          <input type="time" id="daytimeEnd" v-model="daytimeEnd" />
        </div>
  
        <div class="season-setting">
          <label for="currentSeason">Current Season:          
          </label>
          <select v-model="currentSeason">
            <option>Winter</option>
            <option>Spring</option>
            <option>Summer</option>
            <option>Fall</option>
          </select>
        </div>
  
        <div class="metric-setting">
          <label for="temperatureMetric">Temperature Metric:</label>
          <select v-model="temperatureMetric">
            <option>Celsius</option>
            <option>Fahrenheit</option>
          </select>
        </div>
  
        <button @click="saveSettings">Save Settings</button>
      </div>
    </div>
  </template>
  
  <script>
  
  export default {
    data() {
      return {
        email: '', // set to the user's email upon login
        latitude: 0, // set to user's latitude based on their location
        longitude: 0, // set to user's longitude based on their location
        daytimeStart: '08:00', 
        daytimeEnd: '18:00', 
        currentSeason: 'Spring', 
        temperatureMetric: 'Celsius',
      };
    },
    methods: {
      saveSettings() {
        // logic will go here to save the settings
        console.log('Settings saved:', {
          daytimeStart: this.daytimeStart,
          daytimeEnd: this.daytimeEnd,
          currentSeason: this.currentSeason,
          temperatureMetric: this.temperatureMetric,
        });
      },
    },
    mounted() {
      // fetch user data (email, location) when component mounts
      this.email = 'user@example.com'; 
      this.latitude = 37.7749; 
      this.longitude = -122.4194;
    },
  };
  </script>
  
  <style scoped>
  .account-settings {
    padding: 20px;
  }
  .info {
    margin-bottom: 20px;
  }
  .update-options {
    display: flex;
    flex-direction: column;
  }
  .time-setting, .season-setting, .metric-setting {
    margin-bottom: 15px;
  }
  button {
    margin-top: 20px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 10px;
    cursor: pointer;
  }
  button:hover {
    background-color: #45a049;
  }

  </style>
  