<template>
    
    <div>
       <new-meeting-form v-if="newMeeting" @added="addNewMeeting($event)"></new-meeting-form>
       <button v-else @click="showNewMeetingForm()">Dodaj nowe spotkanie</button>
       <meetings-list 
            @joined="joinMeeting($event)" 
            @resign="resignFromMeeting($event)" 
            @delete="deleteMeeting($event)" 
            :meetings="meetings" 
            :user-name="userName" 
            :key="update"></meetings-list>
    </div>

</template>

<script>

import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";
import Vue from 'vue';

export default {

    props: ['userName'],

    components: {
        NewMeetingForm, 
        MeetingsList
    },
  
    data() {
        return {
            meetings: [],
            update: 0,
            newMeeting: false,
        };
    },
  
    methods: {
        addNewMeeting(meeting) {
            this.meetings.push(meeting);
            this.newMeeting = false;
        },

        joinMeeting(meeting) {
            meeting.participants.push(this.userName);
            this.update++;
        },

        resignFromMeeting(meeting) {
            var index;
            index = meeting.participants.indexOf(this.userName);
            meeting.participants.splice(index,1);
            this.update++; 
        },

        deleteMeeting(meeting) {
            var index;
            index = this.meetings.indexOf(meeting);
            this.meetings.splice(index,1);
            this.update++;
        },

        showNewMeetingForm() {
            this.newMeeting = true;
        }
    }
}
</script>