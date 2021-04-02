<template>
  <div class="block" v-if="isShowBlock" @click="stopTimer">
      Click Me
  </div>
</template>

<script>
export default {
    props: ['blockDelay'],
    data() {
        return {
            isShowBlock : false,
            timer : null,
            reactionTime : 0,
        }
    },
    mounted() {
        console.log('Block has mounted')
        setTimeout(()=>{
            this.isShowBlock = true;
            this.startTimer()
            console.log(this.blockDelay)
        } ,this.blockDelay)
    },
    methods: {
        // To count timer in every 10ms
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime += 10;
            },10)
        },
        // When User click "Click me block" it clear timer to default (null)
        stopTimer(){
            clearInterval(this.timer)
            console.log(this.reactionTime)
            this.$emit('stopTimer', this.reactionTime)
        }
    },
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background-color: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
        cursor: pointer;
    }
</style>