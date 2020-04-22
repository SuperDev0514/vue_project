<template>
  <div>
    <h1>Clicked {{ timesClicked }} times.</h1>
    <button @click="iAmClicked()">Click me!</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {timesClicked: 0}
    },
    methods: {
      iAmClicked() {
        this.timesClicked += 1;
      }
    }
  };
</script>
