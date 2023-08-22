<template>

    <button class="click-button">
        {{ title }}
    </button>
    
</template>
    
    
<script>
export default {
    name: "ClickButton",
    props: {
        title: String,
    }
}
</script>


<style scoped>
.click-button{
    background-color: green;
    padding: 20px 30px;
    font-size: 18px;
    color: white;
    font-weight: 500;
    border-radius: 10px;
}
.click-button:hover{
    background-color: rgb(3, 117, 3);
    cursor: pointer;
}
.click-button:disabled{
    background-color: rgb(1, 107, 1);
    cursor: not-allowed;
}
</style>
