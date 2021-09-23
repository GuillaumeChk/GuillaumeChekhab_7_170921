<template>
    <div class="container">
        <button @click="onClick" v-bind:class="(loggingIn)?'selected':''">Se connecter</button>
        <button @click="onClick" v-bind:class="(!loggingIn)?'selected':''">S'enregistrer</button>
        <!-- Connexion -->
        <form @submit="onConnect" v-show="loggingIn">
            <div>
                <label for="">Mail : </label>
                <input type="email" name="mail" pattern="(.+)@(.+){2,}\.(.+){2,}" autofocus required>
            </div>
            <div>
                <label for="">Mot de passe : </label>
                <input type="password" name="password" pattern="^(?=.*[A-Za-z])(?=.*[0-9])([A-Za-z0-9]){8,}$" oninvalid="setCustomValidity('Veuillez entrer au moins 8 caractères dont au moins 1 chiffre.')" required/>
            </div>
            <input class="btn" type="submit" value="Valider">
        </form>
        <!-- Enregistrement -->
        <form @submit="onRegister" v-show="!loggingIn">
            <div>
                <label for="">Prénom : </label>
                <input type="text" name="firstName" required>
            </div>
            <div>
                <label for="">Nom : </label>
                <input type="text" name="lastName" required>
            </div>
            <div>
                <label for="">Mail : </label>
                <input type="email" name="mail" pattern="(.+)@(.+){2,}\.(.+){2,}" required>
            </div>
            <div>
                <label for="">Mot de passe : </label>
                <input type="password" name="password" pattern="^(?=.*[A-Za-z])(?=.*[0-9])([A-Za-z0-9]){8,}$" oninvalid="setCustomValidity('Veuillez entrer au moins 8 caractères dont au moins 1 chiffre.')" required/>
            </div>
            <input class="btn" type="submit" value="Valider">
        </form>
    </div>
</template>

<script>
    export default {
        name: 'Connection',
        data() {
            return {
                loggingIn: true,
            }
        },
        methods: {
            onClick() {
                this.loggingIn = !this.loggingIn
            },
            onConnect(e) {
                e.preventDefault()

                // Afficher les publications si connexion ok
                this.$emit('go-to-posts')
            },
            onRegister(e) {
                e.preventDefault()

                // Afficher les publications si connexion ok
                this.$emit('go-to-posts')
            }
        },
        emits: ['go-to-posts']
    }
</script>

<style lang="scss" scoped>
@import "./src/scss/_variables.scss";
    .container {
        border: 1px solid;
        border-radius: 5px;
        // background-color: $primary-color;
        margin: 10px;
    }
    button {
        border: none;
        background: none;
        width: auto;
        padding: 20px;
        font-size: 1.5rem;
        margin-top: 5px;
        margin-bottom: 20px;
        border-radius: 10px;
        &:hover {
            background-color: $secondary-color;
            color: $color-accent;
        }
    }
    .selected {
        color: $color-accent;
        border-bottom: 2px solid $color-accent;
    }
    div {
        margin-bottom: 15px;
    }
    label {
        color: black;
    }
</style>