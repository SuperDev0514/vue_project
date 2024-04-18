<template>
    <div>
        <h2>Zajęcia</h2>
        <NewMeetingForm @added="addNewMeeting($event)"></NewMeetingForm>
        <MeetingsList :meetings="meetings"></MeetingsList>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: []
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
            }
        }
    }
</script>
