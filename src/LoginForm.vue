<template>
   <div>
       <label>Zaloguj się e-mailem</label>
       <input type="email" v-model="email">
       <button @click="enter()">{{buttonLabelToDisplay}}</button>
   </div>
</template>

<script>
export default {
 props: ['buttonLabel'],
 
 data() {
     return {
		 email: ''
     }
 },

 /*mounted() {
		if (!this.buttonLabel) {
			this.buttonLabel = 'Zaloguj się';
	 }
 },*/
 
 methods: {
     enter() {
         this.$emit('login', this.email);
	 }, 
 },
 
 computed: {
	 buttonLabelToDisplay(){
		 return this.buttonLabel || 'Zaloguj sie';
	 }
 }
}
</script>