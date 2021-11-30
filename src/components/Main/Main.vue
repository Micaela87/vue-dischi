<template>
  <div>
    <div class="container">
      <DiscCard
      v-for="(disc, i) in discs" :key="i"
      :details="disc"/>
    </div>
  </div>
</template>

<script>
import DiscCard from "./DiscCard.vue";

export default {
  name: 'Main',
  components: {
    DiscCard,
  },
  props: {
    discs: Array
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
