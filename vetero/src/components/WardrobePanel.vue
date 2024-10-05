<template>
  <div class="wardrobe-panel">
    <h1>Your Wardrobe</h1>
    <div class="boxes-container">
      <!-- Shirts Box -->
      <div class="box">
        <div class="box-header">
          <h2>Shirts</h2>
          <button @click="openModal('shirt')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in shirt" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button>
            </div>
          </div>
        </div>
      </div>
      <!-- Pants Box -->
      <div class="box">
        <div class="box-header">
          <h2>Pants</h2>
          <button @click="openModal('pants')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in pants" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button></div>
          </div>
        </div>
      </div>
      <!-- Socks Box -->
      <div class="box">
        <div class="box-header">
          <h2>Socks</h2>
          <button @click="openModal('socks')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in socks" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button></div>
          </div>
        </div>
      </div>
      <!-- Shoes Box -->
      <div class="box">
        <div class="box-header">
          <h2>Shoes</h2>
          <button @click="openModal('shoes')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in shoes" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button></div>
          </div>
        </div>
      </div>
      <!-- Jackets Box -->
      <div class="box">
        <div class="box-header">
          <h2>Jackets</h2>
          <button @click="openModal('outershirt')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in outershirt" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button></div>
          </div>
        </div>
      </div>
      <!-- Hats Box -->
      <div class="box">
        <div class="box-header">
          <h2>Hats</h2>
          <button @click="openModal('hat')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in hat" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button></div>
          </div>
        </div>
      </div>
      <!-- Gloves Box -->
      <div class="box">
        <div class="box-header">
          <h2>Gloves</h2>
          <button @click="openModal('gloves')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in gloves" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button></div>
          </div>
        </div>
      </div>
      <!-- Baseshirts Box -->
      <div class="box">
        <div class="box-header">
          <h2>Base Shirts</h2>
          <button @click="openModal('baseshirt')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in baseshirt" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button></div>
          </div>
        </div>
      </div>
      <!-- Baselegs Box -->
      <div class="box">
        <div class="box-header">
          <h2>Base Legs</h2>
          <button @click="openModal('baseleg')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in baseleg" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button></div>
          </div>
        </div>
      </div>
      <!-- Outer Pants Box -->
      <div class="box">
        <div class="box-header">
          <h2>Outer Pants</h2>
          <button @click="openModal('outerleg')">+</button>
        </div>
        <div class="items-container">
          <div class="items-wrapper">
            <div class="item" v-for="(item, index) in outerleg" :key="index">{{ item.itemName }}
              <button @click="editItem(item)">Edit</button></div>
          </div>
        </div>
      </div>
    </div>
    <AddItemModal :isVisible="modalVisible" :isEdit="isItemEdit" :itemInfo="currentItemInfo" @close="closeModal"
      @submit="addItemToCategory" @remove="removeItemFromCategory"/>
  </div>
</template>

<script>
import AddItemModal from './AddItemModal.vue';

export default {
  components: {
    AddItemModal
  },
  data() {
    return {
      shirt: [],
      pants: [],
      shoes: [],
      baseleg: [],
      baseshirt: [],
      outershirt: [],
      outerleg: [],
      hat: [],
      gloves: [],
      socks: [],
      modalVisible: false,
      isItemEdit: false,
      currentCategory: '',
      currentItemInfo: '',
    };
  },
  methods: {
    openModal(category) {
      this.currentCategory = category;
      this.modalVisible = true;
    },
    closeModal() {
      this.isItemEdit = false;
      this.modalVisible = false;
    },
    editItem(item) {
      this.isItemEdit = true;
      this.currentItemInfo = item;
      this.openModal(this.currentCategory);
    },
    removeItemFromCategory(itemInfo) {
      const itemIndex = this[this.currentCategory].findIndex(item => item.itemName === itemInfo.itemName); //use item name to find item in array of category  
      if (itemIndex !== -1) {
            this[this.currentCategory].splice(itemIndex, 1); // remove the item from the category array
        }
    },
    addItemToCategory(itemInfo) {
      //look for exsiting item in array to edit
      const oldItemIndex = this[this.currentCategory].findIndex(item => item.itemName === itemInfo.itemName);
      if (this.isItemEdit) {
        // If the item exists in array
        if (oldItemIndex !== -1) {
          //if the name is being replaced
          if (this.currentItemInfo.itemName !== itemInfo.itemName) {
            this[this.currentCategory].splice(oldItemIndex, 1); // remove the old item
            this[this.currentCategory].push(itemInfo); //insert the new item
          } else {
            //if name is kept the same but other fields are modified, then replace object info
            this[this.currentCategory][oldItemIndex] = { ...itemInfo };
          }
        }

      }
      else {
        // If it doesn't exist, but has the same name as an existing item with the same name
        if (oldItemIndex !== -1) {
          alert('Item with this name exists, please use a different name');

          return;
        } else {
          //new item is being added
          this[this.currentCategory].push(itemInfo);
        }

      }
      console.log("close modal in WardrobePanel");
      this.closeModal();
    }
  }
};
</script>

<style scoped>
.wardrobe-panel {
  padding: 20px;
  font-family: Arial, sans-serif;
  text-align: center;
  height: 80vh;
  overflow-y: auto;
}

.boxes-container {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.box {
  flex: 1;
  margin: 0 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.box-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}

.box-header h2 {
  margin: 0;
}

button {
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 5px 10px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

li {
  padding: 5px 0;
}


.items-container {
  /* entire container for items in category*/
  overflow-y: auto;
  max-height: 200px;
  padding: 5px 0;
}

.items-wrapper {
  /* row container for items in category*/
  display: flex;
  flex-wrap: wrap;
}

.item {
  /* container of item itself*/
  width: calc(20% - 10px);
  /* max width of 5 items per row*/
  margin: 5px;
  padding: 5px 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  background-color: #f9f9f9;
  box-sizing: border-box;
}

/* scroll bar for clothing category container*/
.items-container::-webkit-scrollbar {
  width: 8px;
}

.items-container::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 10px;
}

.items-container::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>
