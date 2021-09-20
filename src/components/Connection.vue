<template>
    <div class="container">
        <button @click="onClick" v-bind:class="(loggingIn)?'selected':''">Se connecter</button>
        <button @click="onClick" v-bind:class="(!loggingIn)?'selected':''">S'enregistrer</button>
        <form @submit="onSubmit">
            <div v-show="!loggingIn">
                <label for="">Prénom : </label>
                <input type="text" name="firstName">
            </div>
            <div v-show="!loggingIn">
                <label for="">Nom : </label>
                <input type="text" name="lastName">
            </div>
            <div>
                <label for="">Mail : </label>
                <input type="text" name="mail">
            </div>
            <div>
                <label for="">Mot de passe : </label>
                <input type="text" name="password">
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
            onSubmit(e) {
                e.preventDefault()

                alert('click')
            }
        }
    }
</script>

<style lang="scss" scoped>
    .container {
        border: 1px solid;
        border-radius: 5px;
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
            background-color: #FFD7D7;
            color: #FD2D01;
        }
    }
    .selected {
        color: #FD2D01;
        border-bottom: 2px solid #FD2D01;
    }
    div {
        margin-bottom: 15px;
    }
    label {
        color: black;
    }
</style>