<template>
  <div class="hello">
    <h1>{{ name }}</h1>
    <h1>{{ description }}</h1>
    <p>Count: {{ count }}</p>
    <button @click="onIncrement">+</button>
    <button @click="onDecrement">-</button>
        <hello-world :msg="message" :person="person" />

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    person: Object,
  },
  data() {
    return {
      message: 'Hi Diana',
      count: 0,
      description: '',
      name: '',
    };
  },
  computed: {
    getMessage() {
      return this.message;
    },
  },
  methods: {
    getMessageMethod() {
      return this.message;
    },
    onDecrement() {
      this.count -= 1;
    },
    onIncrement() {
      this.count += 1;
    },
  },  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
