<template>

   <table>
       <tr>
            <td><h2>Witaj {{userNameToDisplay}} !</h2></td>
            <td><button class="button button-outline" @click="enter()">{{buttonLabelToDisplay}}</button></td>
       </tr>
   </table>

</template>

<script>

export default {

    props: ['userName'], 
 
    methods: {
        enter() {
            this.$emit('logout');
        }, 
    },
 
    computed: {
        buttonLabelToDisplay(){
            return this.buttonLabel || 'Wyloguj sie';
        },
        
        userNameToDisplay(){
            return this.userName || 'ANONYMOUS'
        }
    }
}
</script>