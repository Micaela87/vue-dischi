<template>
  <div id="app">
    <header>
      <img src="./assets/img/spotify-logo.png" alt="spotify logo">
    </header>
    <Discs />
  </div>
</template>

<script>
import Discs from './components/Discs.vue'

export default {
  name: 'App',
  components: {
    Discs
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

header {
  height: 5rem;
  background-color: #2e3a46;
}

header img {
  height: 4.5rem;
  margin: 0.25rem 1rem;
}
</style>
