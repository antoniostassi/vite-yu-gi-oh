<script>
    import AS_Header from './components/AS_Header.vue';
    import AS_Main from './components/AS_Main.vue';
    import AS_Loading from './components/AS_Loading.vue';
    import axios from 'axios';
    import { store } from './store.js';
    import { toRaw } from 'vue'; // Per controllare se il proxy store è vuoto o meno

    export default {
        data(){
            return{
                store
            }
        },
        components:{
            AS_Header,
            AS_Main,
            AS_Loading
        },
        created() {
            axios
            .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
            .then((res) => {
                this.store.allDataCards = res.data.data;

            });
        },
        methods:{
            isStoreEmpty(storeData){
                return toRaw(storeData)
            }
        }
    }
</script>

<template>
    <AS_Header/>
    <AS_Loading v-show="isStoreEmpty(store.allDataCards) == []"/>
    <AS_Main v-if="isStoreEmpty(store.allDataCards) != []"/>
</template>

<style lang="scss">
    @import "bootstrap/scss/bootstrap";
    
</style>
