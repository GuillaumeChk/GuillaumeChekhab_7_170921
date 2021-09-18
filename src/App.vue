<template>
  <img alt="Logo Grouporama" src="../public/icones/icon.svg">
  <h1>Grouporama</h1>
  <Connexion />
</template>

// <script>
import Connexion from './components/Connexion.vue'

export default {
  name: 'App',
  components: {
    Connexion
  }
}
</script>

<style lang="scss">
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  img {
    max-width: 30%;
  }
</style>
