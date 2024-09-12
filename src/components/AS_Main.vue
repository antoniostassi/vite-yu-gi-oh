<script>
    import AS_SingleCard from './AS_SingleCard.vue';
    import AS_Loading from './AS_Loading.vue';
    import { store } from '../store.js';
    export default {
        data(){
            return{
                store
            }
        },
        components:{
            AS_SingleCard,
            AS_Loading
        }
    }
</script>

<template>
    <main class="bg-warning py-5">
        <div class="container-xxl bg-white p-4">
            <div class="bg-black py-2 text-white px-4">
                <span v-show="store.allDataCards != []">Trovate {{ store.allDataCards.length }} carte</span>
            </div>
            <AS_Loading v-if="store.allDataCards == []"/>
            <div v-show="store.allDataCards != []" class="py-2 px-4">
                <div class="my-row d-flex flex-wrap">
                    <AS_SingleCard v-for="(v, i) in store.allDataCards" :cardName="v.name" :cardCategory="v.archetype" :cardImg="v.card_images[0].image_url"/>
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped>
    
</style>
