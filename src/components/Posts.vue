<template>
    <div class="container">
        <div class="head">
            <h2>Publications</h2>
            <button @click="toggleAddPost">{{ btnTexte }}</button>
        </div>
        <AddPost v-show="showAddPost" @submit-post="$emit('add-new-post', newPost)" />
        <div class="container" :key="post.id" v-for="post in posts">
            <h5>{{ post.user }} :</h5>
            <p>{{ post.text }}</p>
        </div>
    </div>
</template>

<script>
    import AddPost from './AddPost.vue'

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
            }
        },
        emits: ['add-new-post']
    }
</script>

<style lang="scss" scoped>
    .container {
        border: 1px solid;
        border-radius: 5px;
        margin-left: 5px;
        margin-right: 5px;
    }
    button {
        width: auto;
        padding: 10px;
        font-size: 1.2rem;
        margin-bottom: 20px;
        background: none;
        width: auto;
        margin-top: 5px;
        margin-bottom: 20px;
        border-radius: 10px;
        color: #FD2D01;
        border: 2px solid #FFD7D7;
        &:hover {
            background-color: #FFD7D7;
        }
    }
    div {
        margin-bottom: 15px;
    }
    .head {
        display: flex;
        justify-content:space-evenly;
        align-items: baseline;
    }
    h5, p {
        color: black;
    }
    h2 {
        color: #FD2D01;
    }
</style>