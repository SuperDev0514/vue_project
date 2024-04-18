<template>
   
    <form @submit.prevent="addNewMeeting()">
        <h3>Dodaj nowe spotkanie</h3>
        <label>Nazwa</label>
        <input type="text" v-model="newMeeting.name">
        <label>Opis</label>
        <textarea v-model="newMeeting.description"></textarea>
        <table>
            <tr>
                <td><button>Dodaj</button></td>
                <td><label class="warning" v-if="nameGiven == false">Spotkanie musi mieć nazwe!</label></td>
            </tr>
        </table>
    </form>

</template>

<script>

export default {
    data() {
        return {
            newMeeting: {participants: []},
            nameGiven: true
        };
    },

    methods: {
        addNewMeeting() {
            if (this.newMeeting.name != null){
                this.$emit('added', this.newMeeting);
                this.newMeeting = {participants: []};
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
