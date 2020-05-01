<template>
    <div v-if="meetings.length > 0">
        <h3>Zaplanowane zajecia ({{meetings.length}})</h3>
        <table>
        <thead>
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <td>{{ meeting.name }}</td>
                <td>{{ meeting.description }}</td>
                <td><ul>
                        <li v-for="participant in meeting.participants">{{participant}}</li></ul></td>
                <td>
                    
                    <button class="button button-outline" v-if="participantSigned(meeting)" @click="resignFromMeeting(meeting)">Wypisz sie</button>
                    <button class="button button-outline" v-else @click="joinMeeting(meeting)">Zapisz sie</button>
                    <button v-if="meeting.participants.length == 0" @click="deleteMeeting(meeting)">Usun puste spotkanie</button>
                </td>

            </tr>
        </tbody>
        </table>
    </div>
    <div v-else>
        <h3>Brak zaplanowanych spotkań</h3>
    </div>
</template>

<script>

export default {

    props: ['meetings', 'userName'],        
    
    methods:{
        joinMeeting(meeting){
            this.$emit("joined", meeting);
        },

        resignFromMeeting(meeting){
            this.$emit("resign", meeting);
        },

        deleteMeeting(meeting){
            this.$emit("delete", meeting);
        },

        participantSigned(meeting){
            var signed = false;
            for (var participant of meeting.participants) {
                if (participant == this.userName) {
                    signed = true;
                }
            }
            return signed;
        }

    },
}
</script>