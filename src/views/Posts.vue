<template>
    <div class="container">
        <div class="head">
            <h2>Publications</h2>
            <button @click="toggleAddPost">{{ btnTexte }}</button>
        </div>
        <!-- publier -->
        <SendPost v-show="showAddPost" @submit-post="addPost" />
        <!-- liste des publications -->
        <div :key="post.id" v-for="post in posts">
            <Post @add-comment="addComment" @delete-post="deletePost" @delete-comment="deleteComment" :post="post" :comments="comments"/>
        </div>
    </div>
    <div class="otherButtons">
        <button @click="onDisconnect" >Se déconnecter</button>
        <button>Supprimer son compte</button>
    </div>
</template>

<script>
import SendPost from '../components/SendPost.vue'
import Post from '../components/Post.vue'

export default {
    name: 'Posts',
    data() {
        return {
            showAddPost: false,
            btnTexte: 'Publier',
            posts: [],
            comments: []
        }
    },
    components: {
        Post,
        SendPost,
    },
    methods: {
        toggleAddPost() {
            this.showAddPost = !this.showAddPost
            if (this.showAddPost) {
                this.btnTexte = 'Annuler'
            }
            else {
                this.btnTexte = 'Publier'
            }
        },
      async addPost(post) {
        await fetch('http://localhost:3000/api/posts', {
          method: 'POST',
          headers: {
            'Content-type': 'application/json',
          },
          body: JSON.stringify(post)
        })
      },
      async deletePost(id) {
        if(confirm('Supprimer cette publication ?')) {
          await fetch(`http://localhost:3000/api/posts/${id}`, {
            method: 'DELETE',
          })

          // Cela supprime également tous les commentaires du post

        }
      },
      async addComment(comment) {
        await fetch('http://localhost:3000/api/comments', {
          method: 'POST',
          headers: {
            'Content-type': 'application/json',
          },
          body: JSON.stringify(comment)
        })
      },
      async deleteComment(id) {
        if(confirm('Supprimer ce commentaire ?')) {
          await fetch(`http://localhost:3000/api/comments/${id}`, {
            method: 'DELETE',
          })
        }
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
      onDisconnect() {
            this.$router.push("/")
        }
    },
    async created() {
      this.posts = await this.fetchPosts()
      this.comments = await this.fetchComments()
    }
}
</script>

<style lang="scss" scoped>
@import "./src/scss/_variables.scss";
    .container {
        border: 1px solid;
        border-radius: 5px;
        margin: 10px;
        padding: 15px;
        // background-color: $primary-color;
    }
    button {
        width: auto;
        padding: 10px;
        font-size: 1.2rem;
        margin-bottom: 20px;
        background: none;
        width: auto;
        margin-top: 5px;
        border-radius: 10px;
        color: $color-accent;
        border: 2px solid $secondary-color;
        &:hover {
            background-color: $secondary-color;
        }
    }
    .head {
        margin-top: 10px;
        display: flex;
        justify-content:space-evenly;
        align-items: baseline;
    }
    h2 {
        color: $color-accent;
    }
    .otherButtons {
        display: flex;
        justify-content: space-evenly;
    }
</style>