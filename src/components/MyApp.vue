<template>
   <Header  />
   <div class="game-container">
     <Figure :wrong-count="wrongLetters.length" />
     <WrongLetters :wrong-letters="wrongLetters" />
     <Word :hints="hints" :letters="letters" :correct-letters="correctLetters" />
   </div>
   <AppPopup :status="status" :word="word" @reset="reset" />
   <Notification :show="notification" />
 </template>
 
 <script>
 import { computed, ref } from 'vue'
 
 import '../assets/style.css'
 
 import Header from './AppHeader.vue'
 import Figure from './AppFigure'
 import WrongLetters from './WrongLetter'
 import Word from './InputWord'
 import AppPopup from './AppPopup'  
 import Notification from './AppNotification'
 
 import onKeydown from '../assets/onKeyDown'

const words =[
  {
       tword:'Red',
       hints:"One of the Three main color"

 },
 {
       tword:'Javascript',
       hints:"One of the demanding Programming language"

 },
 {
      tword:'Mango',
       hints:"One of the favourite fruits for all"

 }

]
const randomIndex = Math.floor(Math.random() * words.length);
 const randomWord =()=> words[randomIndex].tword;
 const randomHints =()=> words[randomIndex].hints;

 
 export default {
   components: { Header, Figure, Word, WrongLetters, AppPopup, Notification },
   setup() {
     const word = ref(randomWord())
     const hints = ref(randomHints())
    
     const guessedLetters = ref([])
 
     const letters = computed(() => word.value.split(''))
    const wrongLetters = computed(() =>
      guessedLetters.value.filter(l => !letters.value.includes(l))
    )
    const correctLetters = computed(() =>
      guessedLetters.value.filter(l => letters.value.includes(l))
    )

    const status = computed(() => {
      if (wrongLetters.value.length === 6) return 'lose'
      if (letters.value.every(l => correctLetters.value.includes(l)))
        return 'win'
      return ''
    })
    const reset = () => {
      guessedLetters.value = []
      word.value = randomWord()
    }

    const notification = ref(false)
    const showNotification = () => {
      notification.value = true
      setTimeout(() => (notification.value = false), 2000)
    }

    onKeydown(event => {
      const letter = event.key.toLowerCase()
      if (event.keyCode < 65 || event.keyCode > 90) return
      if (status.value) return
      if (guessedLetters.value.includes(letter)) {
        showNotification()
        return
      }
      guessedLetters.value.push(letter)
    })

    return {
      letters,
      word,
      wrongLetters,
      correctLetters,
      guessedLetters,
      notification,
      status,
      hints,
      reset
    }
  }
}
</script>