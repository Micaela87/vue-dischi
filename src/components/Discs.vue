<template>
  <div class="container">
    <DiscCard 
    v-for="(disc, i) in discsList" :key="i"
    :details="disc"/>
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
      discsList: []
    };
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
      console.log(this);
      try {
        let response = await axios.get('https://flynn.boolean.careers/exercises/api/array/music');
        console.log(response);
        this.discsList = response.data.response;
      } catch(error) {
        console.log(error);
      }
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
