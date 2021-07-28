<template>
  <div>
    <div class="flex">
      <label>{{label}}:</label>
      <input :type="type" :placeholder="label" :value="value" @input="onInput" />
    </div>
    <div class="message">
      <span v-show="message && message.length">{{message}}</span>
    </div>
  </div>
</template>
<script>
  export default {
    props: ['label', 'type', 'value', 'validateFn'],
    data: function() {
      return {
        message: null
      }
    },
    methods: {
      onInput: function($event) {
        if (this.validateFn) {
          this.message = this.validateFn($event.target.value);
        } 
        this.$emit('input', $event.target.value);
      }
    }
  }
</script>
<style scoped>
  .message {
    color: red;
    /*background-color: #fcc;*/
    padding: 0 0.5rem 0.2rem;
    font-size: 80%;
    height: 1.5rem;
    text-align: right;
  }
  .flex {
    display: flex;
  }
  label {
    flex-basis: 120px;
    margin-right: 0.5rem;
    text-align: right;
  }
  input {
    flex: 1;
  }
</style>
