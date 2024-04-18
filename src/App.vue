<template>

  <div>
    <div>
      <h1>Participants list</h1>
      <ol>
        <li v-for="participant in participants" :key="participant">{{ participant.firstname }} {{ participant.lastname }}</li>
      </ol>
    </div>

    <h3>New participant</h3>
    <form @submit.prevent="addNewParticipant()">
      <label>Firstname</label>
      <input type="text" v-model="newParticipant.firstname">
      <label>Lastname</label>
      <input type="text" v-model="newParticipant.lastname">
      <button>Add new participant</button>
    </form>
=======

  <div>
    <h1>System zapisów na zajecia.</h1>
    <div v-show="authenticatedUserName">
      <logged-user @logout="logout()" :user-name="this.authenticatedUserName"></logged-user>
      <meeting-page :user-name="this.authenticatedUserName"></meeting-page>
    </div>
    <div v-if="authenticatedUserName == ''">
      <login-form @login="login($event)"></login-form>
    </div>

  </div>

</template>

<script>

  export default {
    data() {
      return {
        participants: [],
        newParticipant: {},
      };
    },
    methods: {
      addNewParticipant() {
        this.participants.push(this.newParticipant);
        this.newParticipant = {};
      }
    }
  };
</script>
=======

import "milligram";
import LoginForm from "./LoginForm";
import LoggedUser from "./LoggedUser";
import MeetingPage from "./MeetingPage";

export default {

  components:{
    LoginForm,
    LoggedUser,
    MeetingPage
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
=======
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

