<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>

export default {
    props :['delay'],
    data(){

        return{
            showBlock: false,
            timer : null,
            reactionTime : 0,

        }

    },
    methods:{
        startTimer(){ 
            // every 10ms this func runand add 10ms to this.timer
            this.timer = setInterval(() => {
                this.reactionTime += 10

            } , 10)

        },
        stopTimer(){
            //it fires when click th div
            clearInterval(this.timer)
            //console.log(this.reactionTime)
             //now  we should send this data to parent
             this.$emit('end' , this.reactionTime)

        }
   

    },

    mounted(){
        console.log('component mounted')
        //setTimeout func arg avl hs , arg dovom modt delay bry run shodn func
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)

        } , this.delay)

    },
    /*
    updated(){ // fire when a data update in component
        console.log('component updated')
    },
    onUnmounted(){ // this fire when the component unmounted from the dom 
    // mesle zmni k az app dg neshoon nmide in component
        console.log('component unmounted')
    }
    */

}
</script>

<style>
    .block{
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin:  40px auto;


    }

</style>