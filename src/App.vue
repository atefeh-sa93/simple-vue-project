<template>
  <div id="app">
    <HelloWorld></HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';


export default {
  name: 'app',
  components: {
    HelloWorld,
  },
};
</script>

<style>
  body{
    background: #051838;
    color: #fff;
  }
</style>
