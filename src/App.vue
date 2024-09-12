<script>
    import AS_Header from './components/AS_Header.vue';
    import AS_Main from './components/AS_Main.vue';
    import axios from 'axios';
    import { store } from './store.js';

    export default {
        data(){
            return{
                store
            }
        },
        components:{
            AS_Header,
            AS_Main
        },
        created() {
            axios
            .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
            .then((res) => {
                this.store.allDataCards = res.data.data;
            });
        },
        methods:{
        }
    }
</script>

<template>
    <AS_Header/>
    <AS_Main/>
</template>

<style lang="scss">
    @import "bootstrap/scss/bootstrap";
    
</style>
