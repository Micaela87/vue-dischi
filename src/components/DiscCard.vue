<template>
  <div class="card-container">
    <img src="../assets/img/813JIliG-0L._AC_SL1425_-1024x1024.jpg" alt="pantera">
    <h3>The Great Southern Trendkill</h3>
    <div class="details">
      <div class="artist">Pantera</div>
      <div class="year">1996</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DiscCard',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .card-container {
    width: 15%;
    height: fit-content;
    padding: 1.5rem;
    background-color: #2e3a46;
    text-align: center;
  }

  img {
    max-width: 100%;
  }

  h3 {
    text-transform: uppercase;
    color: white;
    font-size: 1.8rem;
    margin: 1rem 0;
  }

  .details {
    color: #656f76;
  }

  .artist {
    font-size: 1.6rem;
  }

  .yera {
    font-size: 1.4rem;
  }
</style>