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
      },
      async fetchPosts() {
        const res = await fetch('http://localhost:3000/api/posts')
        const data = await res.json()
        return data
      },
      async fetchComments() {
        const res = await fetch('http://localhost:3000/api/comments')
        const data = await res.json()
        return data
      },
      async fetchUsers() {
        const res = await fetch('http://localhost:3000/api/users')
        const data = await res.json()
        return data
      },
    },
    async created() {
      this.users = await this.fetchUsers()
      this.posts = await this.fetchPosts()
      this.comments = await this.fetchComments()
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
