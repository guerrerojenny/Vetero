<template>
    <div class="feedback-content">
      <h2>Feedback</h2>
      <div class="comfort-panel" v-if="!feedbackSubmitted">
        <div class="inner-panel">
          <h3>How comfortable was your outfit on {{date}}</h3>
          <div class="options">
            <button 
              v-for="option in comfortOptions" 
              :key="option.value" 
              :class="['comfort-button', { selected: selectedOption === option.value }]"
              @click="selectOption(option.value)"
            >
              <img :src="getIcon(option.icon)" alt="Emoticon" class="emoticon" />
              <span>{{ option.label }}</span>
            </button>
          </div>
          <button class="submit-button" :disabled="!selectedOption" @click="submitFeedback">Submit</button>
        </div>
      </div>

      <div v-else class="feedback-message">
        Feedback submitted successfully!
      </div>
    </div>
  </template>
  
  <script>
export default {
  props: {
      date: {
        type: String,
        required: true
      },
    },
  data() {
    return {
      comfortOptions: [
        { value: 'too-cold', label: 'Too Cold', icon: 'too-cold.svg' },
        { value: 'just-right', label: 'Just Right', icon: 'just-right.svg' },
        { value: 'too-hot', label: 'Too Hot', icon: 'too-hot.svg' },
      ],
      selectedOption: null,
      feedbackSubmitted: false,
    };
  },
  methods: {
    selectOption(option) {
      this.selectedOption = option;
    },
    submitFeedback() {
      this.feedbackSubmitted = true;
    },
    getIcon(icon) {
      return require(`@/assets/${icon}`);
    },
  },
  name: 'FeedbackPanel'

};
</script>
  
<style scoped>

.feedback-content{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.comfort-panel {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  border: 1px solid #ccc;
  background-color: #f9f9f9;
  border-radius: 8px;
  width: 90%;
}

.inner-panel {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h3 {
  margin-bottom: 10px;
}

.options {
  display: flex;
  gap: 10px;
  margin-bottom: 10px;
}

.comfort-button {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  border: 1px solid #ccc;
  background-color: #fff;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.comfort-button.selected {
  background-color: #e0e0e0;
}

.comfort-button img {
  width: 100%;
  height: 100%;
  margin-bottom: 25%;
}

.submit-button {
  padding: 5px 10px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.submit-button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

.feedback-message {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px;
  border: 1px solid #ccc;
  background-color: #f0fff0;
  border-radius: 8px;
  width: 300px;
  text-align: center;
  color: #4caf50;
  font-weight: bold;
}
</style>
  