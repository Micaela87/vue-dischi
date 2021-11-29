<template>
  <div>
    <SortBy :discList="discGenre" @selectedOption="getGenre"/>
    <div class="container">
      <DiscCard
      v-for="(disc, i) in filteredDiscs" :key="i"
      :details="disc"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import DiscCard from "./DiscCard.vue";
import SortBy from './SortBy.vue';

export default {
  name: 'Discs',
  components: {
    DiscCard,
    SortBy
  },
  data() {
    return {
      discsList: [],
      discGenre: [],
      currentGenre: '',
    };
  },
  computed: {
    filteredDiscs() {
      let filteredList = this.discsList.filter((item) => {
        return item.genre.includes(this.currentGenre);
      });
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
        response.data.response.forEach((item) => {
          if (!this.discGenre.includes(item.genre)) {
            this.discGenre.push(item.genre)
          }
        })
      } catch(error) {
        console.log(error);
      }
    },
    getGenre(param) {
      this.currentGenre = param;
    }
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
