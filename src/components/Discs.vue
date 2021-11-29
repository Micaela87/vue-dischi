<template>
  <div>
    <div class="container">
      <form action="">
        <select name="" id="" v-model="genre">
          <option value="" selected>All</option>
          <option :value="disc" v-for="(disc, y) in discsGenres" :key="y">{{ disc }}</option>
        </select>
      </form>
      <DiscCard
      v-for="(disc, i) in filteredDiscs" :key="i"
      :details="disc"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import DiscCard from "./DiscCard.vue"

export default {
  name: 'Discs',
  components: {
    DiscCard
  },
  data() {
    return {
      discsList: [],
      genre: '',
    };
  },
  computed: {
    discsGenres() {
      let genres = this.discsList.reduce((acc, curr) => {
        if (acc.length === 0 || !acc.includes(curr.genre)) {
          acc.push(curr.genre)
        }
        return acc;
      }, []);
      return genres;
    },
    filteredDiscs() {
      let filteredList = this.discsList.filter((item) => {
        return item.genre.includes(this.genre);
      });
      console.log(filteredList);
      return filteredList;
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
      } catch(error) {
        console.log(error);
      }
    },
    // sortByGenre(event) {
    //   let filteredList = this.discsList.filter((item) => {
    //     console.log(event.target.value);
    //     return item.genre.includes(event.target.value);
    //   });
    //   console.log(filteredList);
    //   return this.discsList = filteredList;
    // }
  },
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
