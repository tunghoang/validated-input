<template>
  <div id="app">
    <ValidatedInput label='Address' type="text" v-model="address" :validateFn="validateAddress" /> 
    <ValidatedInput label='Age' type="number" v-model="age" :validateFn="validateAge" /> 
  </div>
</template>

<script>
import ValidatedInput from './components/ValidatedInput.vue'

export default {
  name: 'App',
  data: function() {
    return {
      address: null,
      age: 10
    }
  },
  components: {
    ValidatedInput
  },
  methods: {
    validateAddress: function(value) {
      if (value.length > 0 && value.length < 10) {
        return null;
      }
      return "Address must be less than 10 characters";
    },
    validateAge: function(value) {
      if (value > 0 && value < 150) {
        return null;
      }
      return "Age must be > 0 and < 150";
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
