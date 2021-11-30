<template>
  <div id="app">
    <Header :genres="genresList" @sendOption="getOption"/>
    <Main :genre="selectedGenre" @sendGenreList="getGenreList"/>
  </div>
</template>

<script>
import Main from './components/Main/Main.vue';
import Header from './components/Header/Header.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return {
      genresList: [],
      selectedGenre: '',
    }
  },
  methods: {
    getOption(value) {
      this.selectedGenre = value;
    },
    getGenreList(arr) {
      this.genresList = arr;
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
