<template>
  <div id="app">
    <Header />
    <Weather />
  </div>
</template>

<script>
import axios from 'axios'
import Weather from './components/Weather'
import Header from './components/Header';

export default {
  name: 'app',
  components: {
    Header,
    Weather


  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
