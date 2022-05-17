<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="increment()">Increment</button>
    <button @click="get">Get Value</button>
    <p>Value is: {{ value }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      value: null
    }
  },
  methods: {
    increment() {
      axios.patch(process.env.VUE_APP_BACKEND_URL + '/value')
    },
    get() {
      axios.get(process.env.VUE_APP_BACKEND_URL + '/value').then(response => this.value = response)
    }
  }
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
