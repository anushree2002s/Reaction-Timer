<template>
    <h2 >Reaction Time:{{ score }} ms</h2>
    <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props:['score'],
    data(){
        return{
        rank: null
    }
},
mounted(){
    if (this.score<250){
        this.rank="Ninja Fingers"
    }else if (this.score<400){
        this.rank="Rapido Fingers"
    }else{
        this.rank="Slow Poke"
    }
}
    

}
</script>

<style>
.rank{
    font-size: 1.4em;
    color:#0faf87;
    font-weight: bolder;
}

</style>