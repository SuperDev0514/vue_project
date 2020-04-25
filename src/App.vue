<template>
  <div>
    <h1>Witaj w systemie zapisów na zajecia.</h1>
    <div v-if="authenticatedUserName">Witaj {{authenticatedUserName}}
    <a @click="logout()"> Wyloguj </a></div>

    <div v-else>Zaloguj sie mailem <input type="email" v-model="email">
    <button @click="login()"> Wchodze </button></div>
  </div>
</template>

<script>

import "milligram";

export default {
  methods: {
    login(){
      this.authenticatedUserName = this.email;
      this.email = '';
    },
    logout() {
      this.authenticatedUserName='';
    }
  },

  data(){
    return{
      email:'',
      authenticatedUserName: ''
    };
  }
}
  
</script>

<style>

</style>
