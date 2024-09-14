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

            axios
            .get('https://db.ygoprodeck.com/api/v7/archetypes.php')
            .then((res) => {
                
                this.store.listArchetypes = res.data;

            });
        },
        methods:{
            isStoreEmpty(storeData){
                return toRaw(storeData)
            },
            getDataWithParams() {

                if (this.store.archetype == "") {
                    this.getDataFromApi();
                    return;
                }

                console.log("Helo??");
                axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0', {
                    params: {
                    archetype: this.store.archetype
                    }
                })
                .then((res) => {
                    this.store.allDataCards = res.data.data;
                })
                .catch((err) => {
                    this.store.allDataCards = [];
                });
            },
            getDataFromApi() {
                axios
                    .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                    .then((res) => {
                        this.store.allDataCards = res.data.data;
                });
            }
        }
    }
</script>

<template>
    <AS_Header/>
    <AS_Loading v-show="isStoreEmpty(store.allDataCards) == []"/>
    <AS_Main @performSearch="getDataWithParams" v-if="isStoreEmpty(store.allDataCards) != []"/>
</template>

<style lang="scss">
    @import "bootstrap/scss/bootstrap";
    
</style>
