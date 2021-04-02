<template>
  <div class="result">
      <p>Reaction Time : {{result}} ms</p>
      <p class="rank">Your rank is : {{rank}}</p>
  </div>
</template>

<script>
export default {
    name : 'Result',
    props : ['result'],
    data() {
        return {
            rank : null,
        }
    },
    mounted() {
        if(this.result < 100){
            this.rank = 'God Reaction'
        }else if(this.result < 250){
            this.rank = 'Good Reaction'
        }else if (this.result < 400){
            this.rank = 'Nice Reaction'
        }else { 
            this.rank = 'Just normal people'
        }
    },
}
</script>

<style>
.rank{
    color: #0faf87;
    font-size: 1.4em;
    font-weight: bold;
}
</style>