<template>
    <div v-if="isVisible" class="modal-overlay">
        <div class="modal">
            <div class="modal-header">
                <h2 class="title">Add Item</h2>
                <button class="close-button" @click="closeModal">X</button>
            </div>
            <div class="modal-body">
                <div class="classification"><label for="name">Name:</label>
                    <input type="text" id="name" v-model="localItemInfo.itemName" placeholder="Enter item name">
                </div>

                <div class="classification"><label for="amount">Amount:</label>
                    <select id="amount" v-model="localItemInfo.itemAmount">
                        <option disabled value="">Please select one</option>
                        <option v-for="n in amountNumbers" :key="n" :value="n">{{ n }}</option>
                    </select>
                </div>

                <div class="classification"><label>Season:</label>
                    <div>
                        <label for="summer">
                            <input type="checkbox" id="summer" value="Summer" v-model="localItemInfo.itemSeason" />
                            Summer
                        </label>
                        <label for="springautum">
                            <input type="checkbox" id="springautum" value="SpringAutum" v-model="localItemInfo.itemSeason" />
                            Spring/Autum
                        </label>
                        <label for="winter">
                            <input type="checkbox" id="winter" value="Winter" v-model="localItemInfo.itemSeason" />
                            Winter
                        </label>
                    </div>
                </div>
                <div class="classification"><label>Waterproof:</label>
                    <div class="checkbox-group">
                        <label>
                            <input type="radio" v-model="localItemInfo.isWaterproof" value="yes"> Yes
                        </label>
                        <label>
                            <input type="radio" v-model="localItemInfo.isWaterproof" value="no"> No
                        </label>
                    </div>
                </div>
                <div class="classification"><label>Requires wash after 1 use:</label>
                    <div class="checkbox-group">
                        <label>
                            <input type="radio" v-model="localItemInfo.needsWash" value="yes"> Yes
                        </label>
                        <label>
                            <input type="radio" v-model="localItemInfo.needsWash" value="no"> No
                        </label>
                    </div>
                </div>
                <div v-if="!isEdit" class="classification"><label for="heatPoints">Heat Points:</label>
                    <select id="amount" v-model="localItemInfo.itemHeatPoints">
                        <option disabled value="">Please select one</option>
                        <option v-for="n in heatPointsNumbers" :key="n" :value="n">{{ n }}</option>
                    </select>
                </div>

            </div>
            <div class="modal-footer">
                <button v-if="isEdit" class="remove-button" @click="remove">Remove Item</button>
                <button @click="submit">Submit</button>
            </div>

        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        isVisible: Boolean,
        isEdit: Boolean,
        itemInfo: {
            type: Object,
            default: () => ({
                itemName: '',
                itemAmount: '',
                itemSeason: [],
                itemWaterproof: '',
                itemWash: '',
                itemHeatPoints: ''
            })
        }
    },
    data() {
        return {
            localItemInfo: this.isEdit ? { ...this.itemInfo } : this.getDefaultItemInfo(),
            amountNumbers: Array.from({ length: 15 }, (_, i) => i + 1),
            heatPointsNumbers: Array.from({ length: 7 }, (_, i) => i + 1)
        };
    }, watch: {
        isVisible(newVal) {
            if (newVal) {
                this.localItemInfo = this.isEdit ? { ...this.itemInfo } : this.getDefaultItemInfo(); // Reset based on isEdit
            }
        }
    },
    methods: {
        getDefaultItemInfo() {
            return {
                itemName: '',
                itemAmount: '',
                itemSeason: [],
                isWaterproof: '',
                needsWash: '',
                itemHeatPoints: ''
            };
        },
        closeModal() {
            this.$emit('close');
            if (!this.isEdit) {
                this.resetFields();
            }
        },
        remove() {
            this.$emit('remove', this.localItemInfo);
        },
        submit() {
            if (!this.isEdit) {
                if (!this.localItemInfo.itemName || !this.localItemInfo.itemAmount ||
                    !this.localItemInfo.itemSeason || !this.localItemInfo.isWaterproof ||
                    !this.localItemInfo.needsWash || !this.localItemInfo.itemHeatPoints) {
                    alert('Please fill in all fields.');
                    return;
                }
            } else {
                if (!this.localItemInfo.itemName || !this.localItemInfo.itemAmount ||
                    !this.localItemInfo.itemSeason || !this.localItemInfo.isWaterproof ||
                    !this.localItemInfo.needsWash) {
                    alert('Please fill in all fields.');
                    return;
                }
            }

            const itemToUpdate = { ...this.localItemInfo };
            this.$emit('submit', itemToUpdate);
            console.log("close modal in AddItemModal")

        }
        ,
        resetFields() {
            this.localItemInfo = { ...this.itemInfo };
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
    margin-left: 145px;
}

.close-button {
    background: none;
    border: none;
    font-size: 20px;
    cursor: pointer;
    background-color: #4CAF50;
    width: 40px;
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
    width: 100%;
}

.remove-button {
    background-color: #f44336;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 10px;
    cursor: pointer;
    margin-right: 238px;
}

.remove-button:hover {
    background-color: #d32f2f;
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
  