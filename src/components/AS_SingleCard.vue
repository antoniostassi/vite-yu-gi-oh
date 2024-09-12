

<script>
    export default {
        data(){
            return{
                cardImg: String,
                cardName: String,
                cardCategory: String
            }
        }
    }
</script>

<template>
    <div class="single-card-info bg-warning mt-4">
        <img :src="cardImg" :alt="cardName">
        <p class="fs-5 p-3 fw-bold text-white text-center"> {{ cardName }}</p>
        <p class="text-center pb-4 fs-5"> {{ cardCategory }} </p>
    </div>
</template>

<style scoped>

</style>
