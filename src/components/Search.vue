<template>
  <!-- <center> -->
    <form action="" method="post" @submit.prevent="submit">
      <input type="text" name="" id="" placeholder="Type something to search for awesome gifs" v-model="keyword" @input="onInput" />
    </form>
  <!-- </center> -->
</template>

<script>
const KEY = "7YD5d8KZmfxpc6gZC6em1fzpMQXQixFV";
export default {
    name: 'Search',
    data() {
      return {
        keyword: '',
        timeout: null
      }
    },
    methods: {
      onInput() {
        clearTimeout(this.timeout);
        this.timeout = setTimeout(() => {
          this.search();
        }, 500)
      },
      search() {
        fetch(`https://api.giphy.com/v1/gifs/search?api_key=${KEY}&q=${this.keyword}&limit=20`).then(response => response.json()).then(result => {
          console.log(result);
          this.$emit('fetch-gifs', result.data);
        })
      }
    }
}
</script>

<style scoped>
  input {
    width: 40%;
    padding: 12px 20px;
    margin: 8px 0;
    box-sizing: border-box;
    border: thin solid #a9a9a925;
    border-radius: 4px;
    background-color: white;
    /* background-image: url('searchicon.png'); */
    background-position: 10px 10px;
    background-repeat: no-repeat;
    padding-left: 40px;
    transition: all .4s ease-in-out;
    outline: none;
    }
  
  input:hover {
    border: 1px solid rgba(153, 153, 153, 0.521);
  }
  
  input:focus {
    outline: none;
    border: 1px solid #999;
    transform: scale(1.2);
    transition: all .4s ease-in-out;
  }
</style>