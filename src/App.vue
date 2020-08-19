<template>
  <div id="app">
    <h1>Cities <span class="diff-color">List</span></h1>
    <list :list="cities" @on-add-city="addCity" @on-save="onSave" @on-delete="onDelete"/>
  </div>
</template>

<script>
import Vue from 'vue';
import List from './components/List.vue';
import uuid from 'uuid';

export default {
  name: 'App',
  components: {
    'list': List,
  },
  data() {
    return {
      cities: [ 
        {
          id: 0,
          name: 'Satu Mare'
        },
        {
          id: 1,
          name: 'Arad'
        },
        {
          id: 2,
          name: 'Timisoara'
        }
        ],
    }
  },

  methods: {
    addCity(city) {
      this.cities.push(city);
    },
    onSave(city) {
      const selectedCity = this.cities.filter(item => item.id === city.id)[0];
      const newCity = {
        id: uuid(),
        name: city.cityName
      };
      let index = this.cities.findIndex(item => item.id === city.id)
      Vue.set(this.cities, index, newCity);
    },
    onDelete(id) {
      let index = this.cities.findIndex(item => item.id === id)
      let deleted = this.cities.splice(index, 1);
    },
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@800&family=Raleway&display=swap');
#app {
  font-family: 'Raleway', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  text-align: center;
}
h1 {
  color: #2A363B;
  font-family: 'Montserrat', sans-serif;
  text-align: center;
  margin-top: 60px;
  margin-bottom: 50px;
}
.diff-color {
  color: #E84A5F;
}
</style>
