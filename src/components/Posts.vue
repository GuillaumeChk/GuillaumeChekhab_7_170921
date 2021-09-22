<template>
    <div class="container">
        <div class="head">
            <h2>Publications</h2>
            <button @click="toggleAddPost">{{ btnTexte }}</button>
        </div>
        <AddPost v-show="showAddPost" @submit-post="addPost" />
        <div :key="post.id" v-for="post in posts">
            <Post @delete-post="deletePost" @delete-comment="deleteComment" :post="post" :comments="comments"/>
        </div>
    </div>
    <button>Supprimer son compte</button>
</template>

<script>
import AddPost from './AddPost.vue'
import Post from './Post.vue'

export default {
    name: 'Posts',
    props: {
        posts: Array,
        comments: Array
    },
    data() {
        return {
            showAddPost: false,
            btnTexte: 'Publier'
        }
    },
    components: {
        Post,
        AddPost,
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
        addPost(post) {
            this.$emit('add-post', post)
        },
        deletePost(id) {
            this.$emit('delete-post', id)
        },
        deleteComment(id) {
            this.$emit('delete-comment', id)
        }
    },
    emits: ['add-post', 'delete-post', 'delete-comment']
}
</script>

<style lang="scss" scoped>
@import "./src/scss/_variables.scss";
    .container {
        border: 1px solid;
        border-radius: 5px;
        margin: 10px;
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
</style>