<template>
  <img alt="Logo Grouporama" src="../public/icones/icon-above-font.svg">
  <Connection v-if="showLoginPage" @go-to-posts="goToPosts" />
  <Posts v-else :posts="posts" :comments="comments" @add-post="addNewPost" @add-comment="addNewComment" @delete-post="deletePost" @delete-comment="deleteComment"  @disconnection="toDisconnect"/>
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
        showLoginPage: true,
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
      },
      addNewComment(comment) {
        this.comments = [...this.comments, comment]
      },
      deleteComment(id) {
        if(confirm('Supprimer ce commentaire ?')) {
          console.log("supprimer " + id)
          // Supprimer la publi
          this.comments = this.comments.filter((comment) => comment.id !== id)
          // Supprimer également tous les commentaires !
        }
      },
      goToPosts() {
        this.showLoginPage = false
      },
      toDisconnect() {
        this.showLoginPage = true
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
          date: '21.09.21',
          hour: '08:05'
        },
        {
          id: 2,
          user: 'Bertrand Jacquard',
          text: "grege",
          date: '21.09.21',
          hour: '14:46'
        },
        {
          id: 3,
          user: 'Cyril Bob',
          text: "tgegregre u ehf uezfz fuez hf izehfeuhf eizuhfuez fez ghiuez ghfiez hfi heuz hexte",
          date: '21.09.21',
          hour: '09:01'
        },
        {
          id: 4,
          user: 'Jean Dupont',
          text: "texgrryeyeyreete",
          date: '21.09.21',
          hour: '14:46'
        },
      ]
      this.comments = [
        {
          id: 1,
          postId: 1,
          user: 'Cyril Bob',
          text: "ça va ?",
          date: '21.09.21',
          hour: '14:46'
        },
        {
          id: 2,
          postId: 1,
          user: 'Jean Dupont',
          text: "peut-etre",
          date: '21.09.21',
          hour: '15:46'
        },
        {
          id: 3,
          postId: 1,
          user: 'Bertrand Jacquard',
          text: "salut c'est moi Bertrand",
          date: '21.09.21',
          hour: '16:46'
        },
        {
          id: 5,
          postId: 3,
          user: 'Cyril Bob',
          text: "ok",
          date: '22.09.21',
          hour: '14:46'
        },
        {
          id: 4,
          postId: 3,
          user: 'Bertrand Jacquard',
          text: "oui",
          date: '22.09.21',
          hour: '18:46'
        },
        
      ]
    }
  }
</script>

<style lang="scss">
@import "./scss/_variables.scss";
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
    color: $primary-color;
    // margin-top: 60px;
  }
  img {
    max-width: 50%;
  }
  input {
    padding: 5px;
  }
  .btn {
    background-color: $secondary-color;
    color: $primary-color;
    border: 2px solid $primary-color;
    border-radius: 5px;
    margin-bottom: 10px;
  }
</style>
