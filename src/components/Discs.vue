<template>
  <div class="container">
    <DiscCard />
  </div>
</template>

<script>
import DiscCard from "./DiscCard.vue"

export default {
  name: 'Discs',
  components: {
    DiscCard
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
    // debugging rules
    height: 50rem;
    background-color: aliceblue;
  }
</style>
