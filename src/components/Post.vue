<template>
    <div class="post">
        <h5>
            {{ post.user }} a dit :
            <span>le {{ post.date }} à {{ post.hour }}</span>
            <i v-show="canDelete" @click="$emit('delete-post', post.id)" class="fas fa-times"></i>
        </h5>
        <p>{{ post.text }}</p>
    </div>
    <Reply @add-comment="addComment" :post="post" />
    <!-- Commentaires -->
    <Comments @delete-comment="deleteComment" :comments="comments" :post="post" />
</template>

<script>
import Comments from './Comments.vue'
import Reply from './Reply.vue'

export default {
    name: 'Post',
    props: {
        post: Object,
        comments: Array,
        
    },
    data() {
        return {
            canDelete: false,
            user: Object,
        }
    },
    components: {
        Comments,
        Reply
    },
    methods: {
        deleteComment(id) {
            this.$emit('delete-comment', id)
        },
        addComment(comment) {
            this.$emit('add-comment', comment)
        },
    },
    async created() {
        if (this.post.user === this.user.userName || this.user.isAdmin) { // est admin ou le créateur du post || post.user
            this.canDelete = true
        }
    },
    emits: ['delete-post','delete-comment', 'add-comment']
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
        margin-top: 12px;
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
        color: red;
    }
</style>