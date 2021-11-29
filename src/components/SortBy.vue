<template>
  <div>
    <form action="">
      <label for="genre">Sort by Genre</label>
      <select name="genre" id="genre" v-model="genre" @change="sendValue">
        <option value="" selected>All</option>
        <option :value="genre" v-for="(genre, y) in filteredGenres" :key="y">{{ genre }}</option>
      </select>
      <label for="artist">Sort by Artist</label>
      <select name="artist" id="artist" v-model="artist" @change="sendValue">
          <option value="">All</option>
          <option :value="artist.author" v-for="(artist, y) in discGenre" :key="y">{{ artist.author }}</option>
      </select>
    </form>
  </div>
</template>

<script>

export default {
  name: 'SortBy',
  props: {
      discList: Array
  },
  data() {
      return {
          genre: '',
          discGenre: this.discList,
          artist: ''
      }
  },
  computed: {
      filteredGenres() {
          console.log(this.discGenre)
          let genres = this.discGenre.reduce((acc, curr) => {
              if (acc.length === 0 || !acc.includes(curr.genre)) {
                  acc.push(curr.genre)
              }
              return acc;
          }, []);
          return genres;
      }
  },
  methods: {
      sendValue() {
          this.$emit('selectedOption', this.genre, this.artist)
      }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    form {
        margin: 1rem;
    }

    label {
        font-size: 1.8rem;
        padding: 0 1rem;
        color: white;
    }
</style>
