<template>
  <img alt="Logo Grouporama" src="../public/icones/icon-above-font.svg">
  <Connection v-if="showLoginPage"/>
  <Posts v-else :posts="posts" @add-post="addNewPost" @delete-post="deletePost"/>
</template>

<script>
  import Connection from './components/Connection.vue'
  import Posts from './components/Posts.vue'

  export default {
    name: 'App',
    components: {
      Connection,
      Posts
    },
    data() {
      return {
        showLoginPage: false,
        posts: []
      }
    },
    methods: {
      addNewPost(post) {
        console.log(post)
        this.posts = [...this.posts, post]
      },
      deletePost(id) {
        if(confirm('Supprimer ce commentaire ?')) {
          console.log("supprimer " + id)
        }
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
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #D1515A;
    // margin-top: 60px;
  }
  img {
    max-width: 50%;
  }
  input {
    padding: 5px;
  }
  .btn {
    background-color: #FFD7D7;
    color: #D1515A;
    border: 2px solid #D1515A;
    border-radius: 5px;
    margin-bottom: 10px;
  }
</style>
