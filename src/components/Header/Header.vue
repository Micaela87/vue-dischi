<template>
  <div>
    <header>
      <img src="@/assets/img/spotify-logo.png" alt="spotify logo">
      <form action="">
            <label for="genre">Sort by Genre</label>
            <select name="genre" id="genre" v-model="selectedGenre" @change="$emit('sendOption', selectedGenre)">
                <option value="" selected>All</option>
                <option :value="genre" v-for="(genre, y) in genres" :key="y">{{ genre }}</option>
            </select>
            <!-- <label for="artist">Sort by Artist</label>
            <select name="artist" id="artist" v-model="artist" @change="sendValue">
                <option value="" selected>All</option>
                <option :value="artist.author" v-for="(artist, y) in filteredDiscs" :key="y">{{ artist.author }}</option>
            </select> -->
        </form>
    </header>
  </div>
</template>

<script>

export default {
  name: 'Header',
  props: {
      genres: Array
  },
  data() {
      return {
          selectedGenre: ''
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    header {
        height: 7rem;
        background-color: #2e3a46;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0.25rem 3rem 0.25rem 1rem;
    }

    header img {
        height: 4.5rem;
    }

    form {
        margin: 1rem;
    }

    label {
        font-size: 1.8rem;
        padding: 0 1rem;
        color: white;
    }
</style>
