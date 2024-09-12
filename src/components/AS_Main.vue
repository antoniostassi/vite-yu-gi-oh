<script>
    import AS_SingleCard from './AS_SingleCard.vue';
    export default {
        data(){
            return{
                cardsInfo: Array,
                loaded: 0
            }
        },
        components:{
            AS_SingleCard
        }
    }
</script>

<template>
    <main class="bg-warning py-5">
        <div class="container-xxl bg-white p-4">
            <div class="bg-black py-2 text-white px-4">
                <span>Trovate {{ loaded }} carte</span>
            </div>
            
            <div class="py-2 px-4">
                <div class="my-row">
                    <div class="my-card-col">
                        <AS_SingleCard v-for="(v, i) in cardsInfo" :cardImg="v.card_images.image_url" :cardName="v.name" :cardCategory="v.archetype"/>
                    </div>
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped>
    .my-card-col {
        width:calc(100%/5);
    }
</style>
