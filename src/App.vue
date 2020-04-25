<template>
  <div>
    <h1>Witaj w systemie zapisów na zajecia.</h1>
    <div v-if="authenticatedUserName">Witaj {{authenticatedUserName}}
    <a @click="logout()"> Wyloguj </a></div>

    <div v-else><login-form @login="login($event)"></login-form></div>
  </div>
  
</template>

<script>

import "milligram";
import LoginForm from "./LoginForm";

export default {
  components:{
    LoginForm
  },

  methods: {
    login(username){
      this.authenticatedUserName = username;
    },
    logout() {
      this.authenticatedUserName='';
    }
  },

  data(){
    return{
      authenticatedUserName: ''
    };
  }
}
  
</script>

<style>

</style>
