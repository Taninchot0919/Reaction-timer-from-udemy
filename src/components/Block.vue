<template>
  <div class="block" v-if="isShowBlock">
      Click Me
  </div>
</template>

<script>
export default {
    props: ['blockDelay'],
    data() {
        return {
            isShowBlock : false
        }
    },
    mounted() {
        console.log('Block has mounted')
        setTimeout(()=>{
            this.isShowBlock = true;
            console.log(this.blockDelay)
        } ,this.blockDelay)
    },
    updated() {
        console.log('updated')
    },
    unmounted() {
        console.log('unmounted')
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
    }
</style>