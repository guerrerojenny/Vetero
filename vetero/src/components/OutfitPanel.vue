<template>
    <div class="outfit-content">
      <h1>Outfit Details</h1>
      <div class="grid">
        <div v-for="(value, key) in outputOutfit()" :key="key" class="item">
        <div class="category">
          {{ key }}
        </div>
        <div class="box">
          {{ value }}
        </div>
      </div> 
    </div>   
  </div>
  </template>
  
  <script>
  export default {
      data() {
      return {
        baseOutfit: {
          shirt: 'short sleeved shirt',
          pants: 'jeans',
          shoes: 'tennis shoes',
          baseleg: '',
          baseshirt: '',
          outershirt: '',
          outerleg: '',
          hat: '',
          gloves: '',
          socks: 'tobilleras',
        }
      };
    },
    methods:{
      outputOutfit(){
        return Object.fromEntries(
          Object.entries(this.baseOutfit).filter(([, value]) => value !== '')
        );
      }
    },
    name: 'OutfitPanel'
  };
  </script>
  
  <style scoped>
.outfit-content {
  text-align: center;
  padding: 20px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px; 
  justify-items: center;
  align-items: center;
}

.item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.category {
  font-weight: bold;
  margin-bottom: 10px;
}

.box {
  padding: 10px 20px;
  background-color: #f0f0f0;
  border-radius: 15px;
  box-shadow: 4px 4px 12px rgba(0, 0, 0, 0.1);
}

</style>

  