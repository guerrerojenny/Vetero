<template>
    <div v-if="isVisible" class="modal-overlay">
        <div class="modal">
            <div class="modal-header">
                <div class="title"></div>
                <h2>Add Item</h2>
                <button class="close-button" @click="closeModal">X</button>
            </div>
            <div class="modal-body">
                <div class="classification"><label for="name">Name:</label>
                    <input type="text" id="name" v-model="itemName" placeholder="Enter item name">
                </div>

                <div class="classification"><label for="amount">Amount:</label>
                    <select id="amount" v-model="itemAmount">
                        <option disabled value="">Please select one</option>
                        <option v-for="n in numbers" :key="n" :value="n">{{ n }}</option>
                    </select>
                </div>
                <div class="classification"><label for="season">Season:</label>
                    <select v-model="selected">
                        <option disabled value="">Please select one</option>
                        <option>Spring</option>
                        <option>Summer</option>
                        <option>Fall</option>
                        <option>Winter</option>
                    </select>
                </div>
                <div class="classification"><label>Waterproof:</label>
                    <div class="checkbox-group">
                        <label>
                            <input type="radio" v-model="isWaterproof" value="yes"> Yes
                        </label>
                        <label>
                            <input type="radio" v-model="isWaterproof" value="no"> No
                        </label>
                    </div>
                </div>
                <div class="classification"><label>Requires wash after 1 use:</label>
                    <div class="checkbox-group">
                        <label>
                            <input type="radio" v-model="needsWash" value="yes"> Yes
                        </label>
                        <label>
                            <input type="radio" v-model="needsWash" value="no"> No
                        </label>
                    </div>
                </div>

            </div>
            <div class="modal-footer">
                <button @click="submit">Submit</button>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        isVisible: Boolean
    },
    data() {
        return {
            itemName: '',
            itemAmount: '',
            selected: '',
            isWaterproof: '',
            needsWash: '',
            numbers: Array.from({ length: 15 }, (_, i) => i + 1)
        };
    },
    methods: {
        closeModal() {
            this.$emit('close');
            this.resetFields();
        },
        submit() {
            if (!this.itemName || !this.itemAmount || !this.selected || !this.isWaterproof || !this.needsWash) {
                alert('Please fill in all fields.');
            } else {
                this.$emit('submit', this.itemName);
                this.closeModal();
            }
        },
        resetFields() {
            this.itemName = '';
            this.itemAmount = '';
            this.selected = '';
            this.isWaterproof = '';
            this.needsWash = '';
        }
    }
};
</script>
  
<style scoped>
.classification {
    margin-bottom: 15px;
    display: flex;
    align-items: center;
    gap: 10px;
    
}

.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
}

.modal {
    background: white;
    border-radius: 8px;
    padding: 20px;
    width: 400px;
    max-width: 100%;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
}

.title {
    display: flex;
    align-items: center;
}

.close-button {
    background: none;
    border: none;
    font-size: 20px;
    cursor: pointer;
    background-color: #4CAF50;
}

.modal-body {
    display: flex;
    flex-direction: column;
    gap: 10px;
    align-items: start;
}

.checkbox-group {
    display: flex;
    gap: 10px;
}

.modal-footer {
    display: flex;
    justify-content: flex-end;
    margin-top: 15px;
}

button {
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
select {
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
}
</style>
  