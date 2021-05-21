<template>
  <Search @fetch-gifs="onFetchGifs" />
  <gif-list :gifs="gifs" />
</template>

<script>
import Search from './components/Search.vue'
import GifList from './components/GifList.vue'
export default {
  name: 'App',
  components: {
    Search,
    GifList
  },
  data() {
    return {
      gifs: []
    }
  },

  methods: {
    onFetchGifs(result) {
      this.gifs = result
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  padding: 50px;
}
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
