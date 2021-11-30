<template>
  <div>
    <div class="container">
      <DiscCard
      v-for="(disc, i) in filteredList" :key="i"
      :details="disc"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import DiscCard from "./DiscCard.vue";

export default {
  name: 'Main',
  components: {
    DiscCard,
  },
  props: {
    genre: String
  },
  data() {
    return {
      discsList: [],
      genresList: []
    }
  },
  computed: {
    filteredList() {
      if (!this.genre) {
        return this.discsList
      }

      return this.discsList.filter((disc) => {
        return disc.genre.includes(this.genre);
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
        this.$emit('sendGenreList', this.genresList);
      } catch(error) {
        console.log(error);
      }
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .container {
    width: 80%;
    margin: 6rem auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
</style>
