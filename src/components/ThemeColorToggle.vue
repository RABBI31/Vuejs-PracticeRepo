<script>
import {computed, inject} from 'vue';
export default {
    setup() {
        const settings = inject("settings")
        const oppositeTheme = computed(()=>
            settings.theme === 'dark' ? 'light' : 'dark'
        )
        const togglemode = () => {
            settings.theme = oppositeTheme.value
        }
       
    
    return{
            settings, oppositeTheme, togglemode
        }
}
}
</script>
<template>
    <button
    :class="{'darkmode' : settings.theme === 'dark'}"
    @click="togglemode"
    >
      switch to {{ oppositeTheme }} corner
    </button>
</template>
<style scoped>
.darkmode{
    color: white;
    background: #000;
}
</style>