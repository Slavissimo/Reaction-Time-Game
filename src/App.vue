<template>
    <h1 class="h1">Reaction Time Game</h1>
    <button class="start-button" @click="start" :disabled="isPlaying">Start</button>
    <p class="countdown" v-if="showCountdown">{{ countdown }}...</p>
    <Block v-if="isPlaying" :delay="delay" @stop="endGame"/>
    <Results v-if="showResults" :score="score"/>
</template>

<script>
    import Block from './components/Block.vue'
    import Results from './components/Results.vue'

    export default {
     name: 'App',
     components: {
      Block,
      Results
     },
     data () {
      return {
       isPlaying: false,
       showCountdown: false,
       countdown: null,
       delay: null,
       score: null,
       showResults: false,
       countdownInterval: null
      }
     },
     methods: {
      start() {
        this.isPlaying = true
        this.showCountdown = true
        this.delay = 3000
        this.countdown = this.delay / 1000
        this.showResults = false
        this.startCountdown()
      },
      startCountdown() {
        this.countdownInterval = setInterval(() => {
          this.countdown--
          if (this.countdown === 0) {
            this.stopCountdown()
            this.showCountdown = false
          }
        }, 1000)
      },
      stopCountdown() {
        clearInterval(this.countdownInterval)
      },
      endGame(reactionTime) {
        this.score = reactionTime
        this.isPlaying = false
        this.showResults = true
      }
     }
    }
    </script>
