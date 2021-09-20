<template>
    <form @submit="onSubmit">
        <label for="text"></label>
        <input type="text" v-model="text" name="text" placeholder="Écrire ici">
        <input class="btn" type="submit" value="Envoyer">
    </form>
</template>

<script>
    export default {
        name: 'AddPost',
        data() {
            return {
                text: '',
            }
        },
        methods: {
            onSubmit(e) {
                e.preventDefault()
                // Si champs vide
                if (!this.text) {
                    alert('Veuillez entrer un message')
                    return
                }

                const newPost = {
                    id: Math.floor(Math.random() * 100000),
                    user: 'testUser',
                    text: this.text,
                }

                console.log(newPost)

                this.$emit('submit-post', newPost)

                // Clear le champs
                this.text = ''
            }
        }

    }
</script>

<style lang="scss" scoped>
    form {
        padding: 15px;
    }
</style>