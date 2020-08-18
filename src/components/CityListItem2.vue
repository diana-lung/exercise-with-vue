<template>
    <div class="city-item"> 
        ID: {{ index }} City Name: {{ name }} 
        <button @click="editCity" :disabled="isEditMode">Edit</button>
        <button @click="$emit('delete-me')" :disabled="isEditMode">Delete</button>
    </div>
</template>

<script>
export default {
    name: 'CityItem',
    props: {
        city: Object,
        isEditMode: Boolean,
    },
    data() {
        return {
            index: this.city.index,
            name: this.city.name,
        }
    },
    methods: {
        editCity() {
            this.$emit('edit-me', this)
        }
    }
}
</script>
   
<style scoped>
.city-item {
    margin-bottom: 10px;
}

button {
    margin-left: 10px;
}
     /* .city-item {

    }
    .city-item:hover {
        cursor: pointer;
        background-color: rgb(111, 139, 216);
    }
    .city-item:focus {
        background-color: rgb(111, 139, 216);;
    } */
</style>