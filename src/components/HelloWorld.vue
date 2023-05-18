<template>
  <div>
   <h1 v-if="characterlist.length>1">There is no Character</h1>
   <div v-else>
    <ul v-for="it in characterlist" :key="it">
      <li v-for="i in it" :key="i">
        {{ i.name }}
        <p v-if="age<50" :style="{ backgroundColor: bgColor }">{{ i.age }}</p>
        <p v-else-if="age<40" :style="{ backgroundColor: bgColor }">{{ i.age }}</p>
        <p v-else :style="{ backgroundColor: bgColor }">{{ i.age }}</p>
        <button @click="incrementAge">
        favourite
      </button>
      </li>
    </ul>
   </div>
  </div>
</template>

<script setup>
import { reactive,ref, onMounted } from 'vue';

const characterlist = reactive({
  character : [{
    name:'tyron lennister',
    age:45,
  },{
    name:'Mother of Dragon',
    age:30
  },{
    name:'Aquamen',
    age:40
  },{
    name:'Thor',
    age:36
  }]
})
const bgColor = ref('')

onMounted(() => {
  // Generate a random color and set it as the background color
  bgColor.value = getRandomColor()
})

function getRandomColor() {
  // Generate a random number between 0 and 255 for each RGB component
  const r = Math.floor(Math.random() * 256)
  const g = Math.floor(Math.random() * 256)
  const b = Math.floor(Math.random() * 256)

  // Return the RGB color as a string in the format 'rgb(r, g, b)'
  return `rgb(${r}, ${g}, ${b})`
}

function incrementAge(){
  characterlist.character.forEach((ele)=>{
    return ele.age++;
  })
}
</script>


<style scoped>

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
