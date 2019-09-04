<template>
  <div id="app">    
    <ul class="nav">
      <li class="nav-item">
        <a v-if="simple" class="nav-link" href="#" v-on:click="toggleView">Quiz</a>
        <a v-if="!simple" class="nav-link" href="#" v-on:click="toggleView">Simple</a>
      </li>
    </ul>
    <div class="container" v-if="!simple">
      <br>
      <h1>Insurance Checker</h1>
      <Form class="center-block" />
    </div>
    <div class="container" v-if="simple">
      <br>
      <h1>Insurance Checker</h1>
      <Simple class="center-block" />
    </div>

  </div>
</template>

<script>
import Form from './components/Form.vue'
import Simple from './components/Simple.vue'
export default {
  name: 'app',
  data: function() {
    return {
      simple: true,
    }
  },
  methods: {
    toggleView: function (event) {
      this.simple = !this.simple;
    }
  },
  components: {
    Form,
    Simple
  }
}
</script>

<style>

</style>
