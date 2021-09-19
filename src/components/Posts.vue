<template>
    <div class="container">
        <h3>Publications</h3>
        <button>Publier</button>
        <AddPost @submit-post="$emit('add-new-post', newPost)" />
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
            posts: Array
        },
        components: {
            AddPost,
        },
        emits: ['add-new-post']
    }
</script>

<style lang="scss" scoped>
    .container {
        border: 1px solid;
        border-radius: 5px;
    }
    button {
        width: auto;
        padding: 10px;
        font-size: 1.2rem;
        margin-bottom: 20px;
    }
    .selected {
        color: rgb(35, 35, 255);
    }
    div {
        margin-bottom: 15px;
    }
</style>