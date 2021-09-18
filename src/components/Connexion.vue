<template>
    <div class="container">
        <h3>Connexion</h3>
        <button class="selected">Se connecter</button>
        <button>S'enregistrer</button>
        <form action="">
        <div>
            <label for="">Mail : </label>
            <input type="text">
        </div>
        <div>
            <label for="">Mot de passe : </label>
            <input type="text">
        </div>
        </form>
    </div>
</template>

<script>
export default {
    name: 'Connexion',
    props: {
        signOrLogIn: Boolean
    }
}
</script>

<style lang="scss" scoped>
    .container {
        border: 1px solid;
        border-radius: 5px;
    }
    button {
        width: auto;
        padding: 20px;
        font-size: 1.5rem;
        margin-bottom: 20px;
    }
    .selected {
        color: rgb(35, 35, 255);
    }
    div {
        margin-bottom: 15px;
    }
</style>