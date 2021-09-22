<template>
    <div class="post">
        <h5>
            {{ post.user }} a dit :
            <i @click="$emit('delete-post', post.id)" class="fas fa-times"></i>
        </h5>
        <p>{{ post.text }}</p>
    </div>
    <!-- Commentaires -->
    <ShowComments @delete-comment="deleteComment" :comments="comments" :post="post" />
</template>

<script>
import ShowComments from './ShowComments.vue'

export default {
    name: 'Post',
    props: {
        post: Object,
        comments: Array,
    },
    components: {
        ShowComments
    },
    methods: {
        deleteComment(id) {
            this.$emit('delete-comment', id)
        }
    },
    emits: ['delete-post','delete-comment']
}
</script>

<style lang="scss" scoped>
@import "./src/scss/_variables.scss";
    .post {
        border: 1px solid;
        border-radius: 5px;
        text-align: left;
        padding: 10px;
        border: none;
        background-color: $secondary-color;
        margin: 15px;
        margin-bottom: 0;
        h5 {
            color:$color-accent;
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
        color: $color-accent;
    }
</style>