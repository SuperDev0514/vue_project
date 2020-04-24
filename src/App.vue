<template>
    <div>
        <h1>Witaj w systemie do zapisów na zajęcia</h1>

        <div v-if="authenticatedUsername">
            <h2>Witaj {{ authenticatedUsername }}</h2>
            <a @click="logMeOut()">Wyloguj</a>
        </div>

        <div v-else>
            <LoginForm @login="(username) => logMeIn(username)" button-label="Wejdź"></LoginForm>
            <LoginForm @login="(username) => logMeIn(username)" button-label="Wleć"></LoginForm>
            <LoginForm @login="(username) => logMeIn(username)"
                        :button-label="Math.random() < 0.5 ? 'Etykieta A' : 'Etykieta B'"></LoginForm>
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
