<template>
    <div>
        <div v-if="isEditMode" class="addArea">
            <p>Edit mode is activated!</p>
            <input text="text" v-model="cityName" />
            <button @click="onSave()">Save</button>
            <button @click="onCancel()">Cancel</button>
        </div>

        <div v-else class="addArea">
            <p>Normal mode is on!</p>
            <input type="text" v-model="city.name" />
            <button  @click="addNewItem">Add</button>
        </div>

        <div v-for="item in list" :key="item.id">
            <city-list-item 
                :track-by="item.id"
                :city="item" 
                :is-edit-mode="isEditMode" 
                @on-edit="onEdit"
                @on-delete="onDelete"
            />
        </div>
    </div>
</template>

<script>
import CityListItem from './CityListItem.vue';
import uuid from 'uuid';

export default {
    name: 'CityList',
    components: {
    'city-list-item': CityListItem,
    },
    props: {
        list: Array,
    },
    data() {
        return {
            isEditMode: false,
            cityName: '',
            id: '',
            city: {
                id: uuid(),
                name: '',
            },
        }
    },

    methods: {
        addNewItem() {
            console.log('addNewItem');
            this.$emit('on-add-city', this.city);
            this.city = { id: uuid(), name: '' };
        },
        deleteItem(index) {
            console.log('deleteItem');
        },
        updateItem(index) {
            console.log('updateItem');
        },
        onSave() {
          const { id, cityName } = this;
          this.$emit('on-save', { id, cityName }); 
          this.isEditMode = false;  
        },
        onCancel() {
          this.isEditMode = false;  
        },        
        onEdit(item) {
            const { name, id } = item;
            this.isEditMode = true;
            this.cityName = name;
            this.id = id;
        },
        onDelete(item) {
            this.$emit('on-delete', item.id);
        },
    },
}
</script>

<style scoped>
.addArea {
    margin-bottom: 30px;
}

.addArea button {
    margin-left: 10px;
}
</style>