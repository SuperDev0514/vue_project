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
=======
    <div>
        <label>Zaloguj się e-mailem</label>
        <input type="email" v-model="email">
        <button @click="enter()">{{ buttonLabel || 'Zaloguj się' }}</button>
    </div>
</template>

<script>
    export default {
        props: {
          buttonLabel: String
        },
        data() {
            return {
                email: ''
            }
        },
        methods: {
            enter() {
                this.$emit('login', this.email);
            }
        }
    }
</script>

