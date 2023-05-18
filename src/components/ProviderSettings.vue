<script>
import {provide,reactive, watch} from 'vue';
export default {
    setup() {
        const settings = reactive({
            theme:'light'
        })
        provide('settings',settings);
        watch(settings, settings =>{
            console.log(`SystemProvider: Change the color of theme ${settings.theme}`)
        })
    },
}
</script>
<template>
    <slot/>
</template>