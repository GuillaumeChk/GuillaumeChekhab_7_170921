<template>
  <img alt="Logo Grouporama" src="../public/icones/icon.svg">
  <h1>Grouporama</h1>
  <!-- <Connection /> -->
  <Posts :posts="posts" />
</template>

<script>
  // import Connection from './components/Connection.vue'
  import Posts from './components/Posts.vue'

  export default {
    name: 'App',
    components: {
      // Connection
      Posts
    },
    data() {
      return {
        posts: []
      }
    },
    created() {
      this.posts = [
        {
          id: 1,
          user: 'Jean',
          text: 'texte',
        },
        {
          id: 2,
          user: 'Cyril',
          text: 'grege',
        },
        {
          id: 3,
          user: 'Bob',
          text: 'tgegregre u ehf uezfz fuez hf izehfeuhf eizuhfuez fez ghiuez ghfiez hfi heuz hexte',
        },
        {
          id: 4,
          user: 'Marcel',
          text: 'texgrryeyeyreete',
        },
      ]
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
