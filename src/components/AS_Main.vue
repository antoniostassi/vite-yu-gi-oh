<script>
    import AS_SingleCard from './AS_SingleCard.vue';

    import { store } from '../store.js';
    export default {
        data(){
            return{
                store
            }
        },
        components:{
            AS_SingleCard
        },
        methods:{
            performSearch() {
                console.log(this.store.archetype);
                this.$emit('performSearch');
            }
        }
        
    }
</script>

<template>
    <main class="bg-warning py-5">
        
        <div class="container-xxl bg-white p-4">
            <form @submit.prevent="performSearch()">
                <select v-model="store.archetype" class="mb-3">
                    <option value="">Select archetype</option>
                    <option @click="store.archetype = v.archetype_name" v-for="(v, i) in store.listArchetypes" :key="i" :value="v.archetype_name"> {{ v.archetype_name }}</option>
                </select>
                <button type="submit" class="btn btn-primary ms-2 p-1">Filter</button>
                <button @click="store.archetype = '' " type="submit" class="btn btn-primary ms-2 p-1">Reset</button>
            </form>
            
            <div class="bg-black py-2 text-white px-4">
                <span v-show="store.allDataCards != []">Trovate {{ store.allDataCards.length }} carte</span>
            </div>
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
