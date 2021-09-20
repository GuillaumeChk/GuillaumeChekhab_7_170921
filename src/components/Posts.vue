<template>
    <div class="container">
        <div class="head">
            <h2>Publications</h2>
            <button @click="toggleAddPost">{{ btnTexte }}</button>
        </div>
        <AddPost v-show="showAddPost" @submit-post="addPost" />
        <div :key="post.id" v-for="post in posts">
            <Post @delete-post="deletePost" :post="post"/>
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
        }
    },
    emits: ['add-post', 'delete-post']
}
</script>

<style lang="scss" scoped>
    .container {
        border: 1px solid;
        border-radius: 5px;
        margin: 10px;
    }
    button {
        width: auto;
        padding: 10px;
        font-size: 1.2rem;
        margin-bottom: 20px;
        background: none;
        width: auto;
        margin-top: 5px;
        // margin-bottom: 20px;
        border-radius: 10px;
        color: #FD2D01;
        border: 2px solid #FFD7D7;
        &:hover {
            background-color: #FFD7D7;
        }
    }
    .head {
        margin-top: 10px;
        display: flex;
        justify-content:space-evenly;
        align-items: baseline;
    }
    h2 {
        color: #FD2D01;
    }
</style>