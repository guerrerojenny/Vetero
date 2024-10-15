<template>
  <div class="outfit-content" >
    <h1>Outfit Details</h1>
    <div v-if=outputOutfit() class="outfit">
      <div v-for="(value, key) in outfit" :key="key" class="item">
        <div class="category">
          {{ key }}
        </div>
        <div class="box">
          {{ value }}
        </div>
      </div> 
    </div> 
    <div v-else class="no-outfit">
      <h1>No Outfit for Today</h1>
      <h2>Make sure you have added clothes to your wardrobe</h2>
    </div>  
  </div>
</template>
  
  <script>
  export default {
      data() {
      return {
        isEmpty: false,
        baseOutfit: {
          'shirt': 'none',
          'pants': 'none',
          'shoes': 'none',
          'baseleg': 'none',
          'baseshirt': 'none',
          'outershirt': 'none',
          'outerleg': 'none',
          'hat': 'none',
          'gloves': 'none',
          'socks': 'none',
        },
        outfit: null
      };
    },
    methods:{
      outputOutfit(){
        this.outfit =  Object.fromEntries(
          Object.entries(this.baseOutfit).filter(([, value]) => value !== 'none')
        );
        if(Object.keys(this.outfit).length == 0){
          return false
        }
        return true;
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

.outfit {
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

  