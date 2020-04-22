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
