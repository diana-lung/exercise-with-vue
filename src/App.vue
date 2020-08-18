<template>
  <div id="app">
    <h1>Cities <span class="diff-color">List</span></h1>
    <list :list="cities" @on-add-city="addCity" @on-save="onSave" />
  </div>
</template>

<script>
import Vue from 'vue';
import List from './components/List.vue'

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
      console.log(city, 'city');
      const selectedCity = this.cities.filter(item => item.id === city.id)[0];
      selectedCity.name = city.cityName;
      console.log(this.cities, 'cities');
      Vue.set(this.cities, 0, selectedCity)
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
