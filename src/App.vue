<template>
  <div>
    <h1>Witaj w systemie zapisów na zajecia.</h1>
    <div v-if="loggeged == 0">Zaloguj sie mailem <input type="email" v-model="email">
    <button @click="login()"> Wchodze </button></div>
    <div v-else>Witaj {{email}}
    <button @click="logout()"> Wyloguj </button></div>
  </div>
</template>

<script>
export default {
  methods: {
    login(){
      this.loggeged=1
    },
    logout() {
      this.loggeged=0
      this.email = ''
    }
  },

  data(){
    return{
      email:'',
      loggeged:0
    };
  }
}
  
</script>

<style>

</style>
