<script setup>

import { customRef } from 'vue';

const isemail = value => value.includes('@');

const email = customRef((track,trigger)=>{
    let value = null;

    return{
        get(){
            track()
            return value;
        },
        set(input){
            if(isemail(input)){
                value =input
                trigger()
            }
        }
    }
    
})
email.value = 'invalid'
console.log(email.value)
email.value = "rabbi@softzinom.com"
console.log(email.value)

</script>
<template>
    <button @click="increment">{{ counter }}</button>
    <p>{{ arrayofEmoji }}</p>

</template>



<style scoped>
 *{
    margin: 0;
    padding: 0;
 }
</style>