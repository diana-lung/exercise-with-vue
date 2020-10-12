<template>
  <div id="app">
    <h1>Person <span class="diff-color">Data</span></h1>
    <person-data />
  </div>
</template>

<script>
import Person from './components/Person.vue';

export default {
  name: 'App',
  components: {
    'person-data': Person,
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
