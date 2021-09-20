<template>
    <div class="post">
        <h5>
            {{ post.user }} :
            <i @click="$emit('delete-post', post.id)" class="fas fa-times"></i>
        </h5>
        <p>{{ post.text }}</p>
    </div>
    <!-- Commentaires ici ? -->
    <div :key="comment.id" v-for="comment in comments">
        <Comment :comment="comment" />
    </div>
</template>

<script>
import Comment from './Comment.vue'

export default {
    name: 'Post',
    props: {
        post: Object,
        comments: Array,
    },
    components: {
        Comment
    },
    emits: ['delete-post']
}
</script>

<style lang="scss" scoped>
    .post {
        border: 1px solid;
        border-radius: 5px;
        text-align: left;
        padding: 10px;
        border: none;
        background-color: #FFD7D7;
        margin: 15px;
        margin-bottom: 0;
        h5 {
            color:#FD2D01;
            margin-bottom: 5px;
        }
    }
    h5, p {
            color: black;
    }
    h5 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .fas {
        color: red;
    }
    .comment {
        text-align: left;
        width: 100%;
        margin-left: 30px;
        button {
            padding: 3px;
            padding-left: 10px;
            padding-right: 10px;
            background-color: white;
            color: #FD2D01;
            border: 2px solid #FFD7D7;
            border-bottom-left-radius: 5px;
            border-bottom-right-radius: 5px;
            border-top: none;
        }
    }
</style>