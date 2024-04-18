<template>
    <ul>
        <li v-for="participant in participants" :key="participant">{{participant}}</li> 
    </ul>
</template>

<script>
export default {
    props: ['participants'],
}
</script>