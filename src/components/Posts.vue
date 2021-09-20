<template>
    <div class="container">
        <div class="head">
            <h2>Publications</h2>
            <button @click="toggleAddPost">{{ btnTexte }}</button>
        </div>
        <AddPost v-show="showAddPost" @submit-post="addPost" />
        <div class="post" :key="post.id" v-for="post in posts">
            <h5>
                {{ post.user }} :
                <i @click="$emit('delete-post', post.id)" class="fas fa-times"></i>
                </h5>
            <p>{{ post.text }}</p>
        </div>
    </div>
    <button>Supprimer son compte</button>
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
            },
            addPost(post) {
                this.$emit('add-post', post)
            }
        },
        emits: ['add-post', 'delete-post']
    }
</script>

<style lang="scss" scoped>
    .container, .post {
        border: 1px solid;
        border-radius: 5px;
        margin-left: 5px;
        margin-right: 5px;
    }
    .post {
        text-align: left;
        padding: 10px;
        border: none;
        background-color: #FFD7D7;
        h5 {
            color:#FD2D01;
            margin-bottom: 5px;
        }
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
    h5 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .fas {
        color: red;
    }
</style>