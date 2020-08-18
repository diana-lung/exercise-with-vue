<template>
    <div class="city-item"> 
        ID: {{ id }} City Name: {{ name }} 
        <button @click="this.$emit('on-edit', this.city)" :disabled="isEditMode">Edit</button>
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
            id: this.city.id,
            name: this.city.name,
        }
    },
}
</script>
   
<style scoped>
.city-item {
    margin-bottom: 10px;
}

button {
    margin-left: 10px;
}
</style>