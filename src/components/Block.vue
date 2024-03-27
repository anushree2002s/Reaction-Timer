<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        CLICK ME
    </div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return{
            showBlock:false, //this is false ATM bc we don't wanna show the block right away. but rather after some delay
            timer: null,
            reactionTime:0
        }
    },
    mounted(){
        //this mounted happens only when u press the play button. this means the block has been mounted on the DOM
        //now we're setting up a timer so that the block can be visible after a small amount of delay and shows us the updated comment
        setTimeout(()=>{
            this.showBlock= true
            this.startTimer() //this function now starts the timer bc the block is now mounted on the DOM
        }, this.delay)
    },
    // updated(){ //this fires only when a certain data is updated in our DOM
    //     console.log("component upated")
    // }
   methods:{
    startTimer(){
        this.timer= setInterval(()=>{
            this.reactionTime += 10
        }, 10)

    },
    stopTimer(){
        clearInterval(this.timer) //when u clear the interval, the this.timer function will not fire.
        console.log(this.reactionTime)
        this.$emit('endTime', this.reactionTime)
    }
   }

}
</script>

<style>
.block{
    width: 300px;
    background-color: #067257;
    border-radius: 20px;
    color: white;
    margin: 40px auto;
    padding: 100px 0;
    text-align: center;
    font-weight: bold;
}

</style>