

<script>
    export default {
        data(){
            return{
                
            }
            
        },
        props:{
            cardImg: String,
            cardName: String,
            cardCategory: String
        }
    }
</script>

<template>
    <div class="my-card-col bg-warning mt-4">
        <img :src="cardImg" :alt="cardName">
        <p class="fs-5 p-3 fw-bold text-white text-center"> {{ cardName }}</p>
        <div class="text-center">
            <p class="fs-5"> {{ cardCategory }} </p>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.my-card-col {
    margin:0 20px;
    width:calc(100%/5 - 40px);    
}
</style>
