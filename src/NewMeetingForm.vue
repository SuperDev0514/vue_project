<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <table><tr>
            <td><button>Dodaj</button></td>
            <td><label class="warning" v-if="nameGiven == false">Spotkanie musi mieć nazwe!</label></td>
            </tr></table>
        </form>
</template>

<script>
export default {
  data() {
      return {
          newMeeting: {},
          nameGiven: true
      };
  },

  methods: {
      addNewMeeting() {
        if (this.newMeeting.name != null){
            this.newMeeting.participants = [];
            this.$emit('added', this.newMeeting);
            this.newMeeting = {};
            this.nameGiven = true;
        } else {
            this.nameGiven = false;
        }
    }
  }
}
</script>

<style>
label.warning {
    color: red;
}
</style>