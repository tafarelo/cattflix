<template>
  <div id="app">
    <div v-for="item in this.arrayGifs" :key="item.images.original.url">
      <img alt="Vue logo" :src="item.images.original.url" height="200" width="200">
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'App',
  data: () => {
    return {
      arrayGifs: [],
    }
  },
  created() {
    axios.get('http://api.giphy.com/v1/gifs/search?api_key=dc6zaTOxFJmzC&q=cat')
    .then((response) => {
      this.arrayGifs = response.data.data
      console.log(this.arrayGifs);
    }).catch((err) => {
      console.log(err);
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
