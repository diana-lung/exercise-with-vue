<template>
    <div>
        <div v-for="(item, index) in list" :key="index">
      {{item.name}} {{item.index}}
      </div>

        <div v-if="isEditMode" class="addArea">
            <p>Edit mode is activated!</p>
            <input text="text" v-model="propriety"/>
            <button @click="isEditMode = false, updateItem(index)">Save</button>
            <button @click="isEditMode = false">Cancel</button>
        </div>

        <div v-if="!isEditMode" class="addArea">
            <p>Normal mode is on!</p>
            <input type="text" v-model="propriety">
            <button  @click="addNewItem">Add</button>
        </div>

        <div v-for="(item,idx) in list" :key="item.index">
            <city-list-item :city="item" :isEditMode="isEditMode" 
             @delete-me="deleteItem(idx)" 
             @edit-me="propriety=$event.name, index=$event.index, isEditMode = true"/>
        </div>
    </div>
</template>

<script>
import CityListItem from './CityListItem.vue'

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
            ID: 2,
            propriety: '',
            index: 0,
        }
    },
    methods: {
         addNewItem() {
            if (this.propriety != '') {
                this.ID += 1;
                this.list.push({
                index: this.ID,
                name: this.propriety,
                })
            } else alert('Please give a city name!');
        },
        deleteItem(index) {
            this.$delete(this.list, index);
        },
        updateItem(index) {
            if (this.propriety != ''){
                this.list[index].name = this.propriety;
            } else alert('Please give a name!');
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