<template>
    <h3>Score :  {{ score }}ms </h3>
    <h1> {{ rank }} </h1>
</template>

<script>
export default {
    props: [ 'score' ],
    data(){
        return{
            rank: null,
        }
    },
    mounted(){
        if(this.score < 200){
            this.rank = 'Impressive'
        }
        else if(this.score < 500){
            this.rank = 'Pretty Good'
        }
        else{
            this.rank = 'snail left the chat'
        }
    }

}
</script>

<style>

</style>