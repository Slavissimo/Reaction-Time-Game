<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click me!
  </div>
</template>
<script>
export default {
    data() {
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0,
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            this.showCountdown = false
        }, this.delay)
    },
    props: ['delay'],
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 1
            }, 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('stop', this.reactionTime)
        }
    }
}
</script>
<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background-color: green;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>