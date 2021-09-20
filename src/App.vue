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
        users: [],
        posts: [],
        comments: []
      }
    },
    methods: {
      addNewPost(post) {
        this.posts = [...this.posts, post]
      },
      deletePost(id) {
        if(confirm('Supprimer cette publication ?')) {
          console.log("supprimer " + id)
          // Supprimer la publi
          this.posts = this.posts.filter((post) => post.id !== id)
          // Supprimer également tous les commentaires !
        }
      }
    },
    created() {
      this.users = [
        {
          name: 'Jean Dupont',
          mail: 'jeand@mail.fr',
          password: 'jeanjean1'
        },
        {
          name: 'Bertrand Jacquard',
          mail: 'bertj@mail.fr',
          password: 'bertbert2'
        },
        {
          name: 'Cyril Bob',
          mail: 'cyrib@mail.fr',
          password: 'cyricyri3'
        }
      ]
      this.posts = [
        {
          id: 1,
          user: 'Jean Dupont',
          text: "texte",
        },
        {
          id: 2,
          user: 'Bertrand Jacquard',
          text: "grege",
        },
        {
          id: 3,
          user: 'Cyril Bob',
          text: "tgegregre u ehf uezfz fuez hf izehfeuhf eizuhfuez fez ghiuez ghfiez hfi heuz hexte",
        },
        {
          id: 4,
          user: 'Jean Dupont',
          text: "texgrryeyeyreete",
        },
      ]
      this.comments = [
        {
          id: 1,
          postId: 1,
          user: 'Cyril Bob',
          text: "ça va ?"
        },
        {
          id: 2,
          postId: 1,
          user: 'Jean Dupont',
          text: "peut-etre"
        },
        {
          id: 3,
          postId: 1,
          user: 'Bertrand Jacquard',
          text: "salut c'est moi Bertrand"
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
