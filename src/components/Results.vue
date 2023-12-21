<template>
  <p class="results">Results: {{ score }}ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 100) {
            this.rank = 'Godlike'
        } 
        else if(this.score < 250) {
            this.rank = 'Ninja Fingers'
        } 
        else if(this.score < 400) {
            this.rank = 'Not so bad...'
        }
        else {
            this.rank = 'Snail pace...'
        }
    },
}
</script>

<style>

</style>