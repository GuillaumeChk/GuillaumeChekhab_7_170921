<template>
    <form @submit="onSubmit">
        <label for="text"></label>
        <input type="text" v-model="text" name="text" placeholder="Votre message ici">
        <input class="btn" type="submit" value="Envoyer">
    </form>
</template>

<script>
    export default {
        name: 'SendPost',
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

                // Formatage date et heure
                const fullDate = new Date()
                const date = fullDate.getUTCDate() + '.' + fullDate.getUTCMonth() + '.' + fullDate.getYear()
                const hour = fullDate.getUTCHours() + ':' + fullDate.getUTCMinutes()

                // Créer l'objet post
                const post = {
                    id: Math.floor(Math.random() * 100000),
                    user: 'testUser',
                    text: this.text,
                    date: date,
                    hour: hour,
                }

                this.$emit('submit-post', post)

                // Clear le champs
                this.text = ''
            }
        }
    }
</script>

<style lang="scss" scoped>
@import "./src/scss/_variables.scss";
    form {
        padding: 15px;
    }
</style>