<template>
    <div>
        <h2>Witaj {{ username }}</h2>
        <a @click="$emit('logout')">Wyloguj</a>
    </div>
</template>

<script>
    export default {
        props: {
          username: String,
        }
    }
</script>
