<template>
    <div>
        <h1>Twój e-mail to {{ email }}</h1>
        <input type="email" v-model="email">
    </div>
</template>

<script>
    export default {
        data() {
            return {
                email: ''
            }
        }
    }
</script>
