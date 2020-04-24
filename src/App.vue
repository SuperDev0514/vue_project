<template>
    <div>
        <h1>Witaj w systemie do zapisów na zajęcia</h1>

        <div v-if="authenticatedUsername">
            <h2>Witaj {{ authenticatedUsername }}</h2>
            <a @click="logMeOut()">Wyloguj</a>
        </div>

        <div v-else>
            <LoginForm @login="(username) => logMeIn(username)"></LoginForm>
        </div>
    </div>
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";

    export default {
        components: {LoginForm},
        data() {
            return {
                authenticatedUsername: '',
            }
        },
        methods: {
            logMeIn(username) {
                this.authenticatedUsername = username;
            },
            logMeOut() {
                this.authenticatedUsername = '';
            }
        }
    }
</script>
