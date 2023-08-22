<template>
    <div class="results">
        <h3>Reaction time is {{ score }} ms.</h3>

        <h1>
            {{ rank }}            
        </h1>
    </div>
</template>

<script>
export default {
    name: "ResultsBlock",
    props: ["score"],
    data(){
        return {
            rank: null
        }
    },
    mounted(){
        if (this.score < 250){
            this.rank = "Very Fast!"
        } else if (this.score < 500){
            this.rank = "Fast!"
        } else if (this.score < 750){
            this.rank = "Normal!"
        } else {
            this.rank = "Slow!"
        }
    }
}
</script>


<style scoped>
h1{
    text-align: center;
    padding: 20px 0px;
    color: aqua;
    font-size: 30px;
    font-weight: 600;
}
</style>