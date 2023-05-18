<template>
  <div style="margin-top: 100px;">
      <p>Hints for the letter</p>
      {{ hints }}
    </div>
    <div class="word">
      <span class="letter" v-for="(letter=0, i) in letters" :key="i">
        {{ correctLetters.includes(letter) ? letter : '' }}
      </span>
    </div>
    
  </template>
  
  <script>
  export default {
    props: {
      hints:{ type: String, required: true},
      letters: { type: Array, required: true },
      correctLetters: { type: Array, default: () => [] }
    }
  }
  </script>