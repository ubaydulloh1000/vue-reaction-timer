<template>

<div class="block" v-if="showBlock" @click="stopTimer">
    <h1>click me!</h1>
</div>

</template>


<script>
export default {
    name: "GameBlock",
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTime: null
        }
    },
    props: ["delay"],
    methods:{
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime += 5
            }, 5)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit("endGame", this.reactionTime)
        }
    },

    mounted(){
        console.log("Component mounted!")
        setTimeout(()=> {
            this.showBlock = true
            this.reactionTime = null
            this.startTimer()
        }, this.delay)
    },
    updated(){
        console.log("Component updated!")
    }
}
</script>

<style scoped>
.block {
    margin: 100px auto;
    width: 500px;
    height: 400px;
    background-color: green;
    padding: 30px 0px;
}
.block h1{
    text-align: center;
    color: white;
    font-size: 20;
}
</style>
