<template>
  <p>Reaction Time - {{ score }} ms</p>
  <p class="rank"> {{ rank }}</p>
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
        if (this.score < 270){
            this.rank = 'Wow! Very fast!'
        }else if (this.score < 400) {
            this.rank = 'Pretty fast!'
        } else {
            this.rank = 'Kind of slow.'
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>