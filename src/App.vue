<template>
  <div id="app">
    <Header :genres="genresList" @sendOption="getOption"/>
    <Main :discs="filteredList"/>
  </div>
</template>

<script>
import axios from 'axios';
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
      discsList: [],
      genresList: [],
      selectedGenre: '',
    }
  },
  computed: {
    filteredList() {
      if (!this.selectedGenre) {
        return this.discsList
      }

      return this.discsList.filter((disc) => {
        return disc.genre.includes(this.selectedGenre);
      });
    }
  },
  created() {
    this.getDiscs();
  },
  methods: {
    // getDiscs() {
    //   axios.
    //   get('https://flynn.boolean.careers/exercises/api/array/music')
    //   .then((response) => {
    //     this.discsList = response.data.response;
    //   })
    //   .catch((error) => {
    //     console.log(error);
    //   })
    // }
    getDiscs: async function() {
      try {
        let response = await axios.get('https://flynn.boolean.careers/exercises/api/array/music');
        this.discsList = response.data.response;
        this.genresList = this.discsList.reduce((acc, curr) => {
          if (acc.length === 0 || !acc.includes(curr.genre)) {
            acc.push(curr.genre);
          }
          return acc;
        }, []);
      } catch(error) {
        console.log(error);
      }
    },
    getOption(value) {
      this.selectedGenre = value;
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
