<template>
<h1>Sana reaction timer</h1>
<button @click="start" :disabled="isPlaying" >play</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame"/>
<Results v-if="showResult" :score="score" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'


export default {
  name: 'App',
  components: {Block, Results },
  data(){
    return {
      isPlaying : false ,
      showResult : false,
      delay :null,
      score: null
    }

  },
  methods:{
    start(){
      this.delay = 2000 + Math.random()*5000 // math.randoom is between 0 to 1 so delay is between 2 to 7s
      this.isPlaying = true
      this.showResult =false
      //console.log(this.delay)

    },

    endGame(reactionTime){ // we emit reactionTime in Block and now we get it loke arg in this func
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
      //console.log(this.isPlaying)



    }

  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button{
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;

}
button[disabled]{
opacity: .2;
cursor: not-allowed;

}
</style>
