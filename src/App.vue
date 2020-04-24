<template>
    <div>
        <h1>Witaj w systemie do zapisów na zajęcia</h1>

        <div v-if="authenticatedUsername">
            <h2>Witaj {{ authenticatedUsername }}</h2>
            <a @click="logMeOut()">Wyloguj</a>
        </div>

        <div v-else>
            <label>Zaloguj się e-mailem</label>
            <input type="email" v-model="email">
            <button @click="logMeIn()">Wchodzę</button>
        </div>

    </div>
</template>

<script>
    export default {
        data() {
            return {
                authenticatedUsername: '',
                email: ''
            }
        },
        methods: {
            logMeIn() {
                this.authenticatedUsername = this.email;
                this.email = '';
            },
            logMeOut() {
                this.authenticatedUsername = '';
            }
        }
    }
</script>
