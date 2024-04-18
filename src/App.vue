<template>
    <div>
        <h1>Witaj w systemie do zapisów na zajęcia</h1>

        <div v-if="authenticatedUsername">
            <UserPanel :username="authenticatedUsername" @logout="logMeOut()"></UserPanel>
            <MeetingsPage></MeetingsPage>
        </div>

        <div v-else>
            <LoginForm @login="(username) => logMeIn(username)"></LoginForm>
        </div>
    </div>
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import UserPanel from "./UserPanel";
    import MeetingsPage from "./meetings/MeetingsPage";

    export default {
        components: {LoginForm, MeetingsPage, UserPanel},
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
