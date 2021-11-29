<template>
  <div>
    <form action="">
      <label for="genre">Sort by Genre</label>
      <select name="genre" id="genre" v-model="genre" @change="sendValue">
        <option value="" selected>All</option>
        <option :value="disc" v-for="(disc, y) in discGenre" :key="y">{{ disc }}</option>
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
          discGenre: this.discList
      }
  },
  methods: {
      sendValue() {
          this.$emit('selectedOption', this.genre)
      }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    label {
        font-size: 1.2rem;
        padding: 0 1rem;
    }
</style>
