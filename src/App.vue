<script>
    import AS_Header from './components/AS_Header.vue';
    import AS_Main from './components/AS_Main.vue';
    import axios from 'axios';

    export default {
        data(){
            return{
                yugiData: []
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
                this.yugiData = res.data.data;
            });
        }
    }
</script>

<template>
    <AS_Header/>
    <AS_Main :cardsInfo="yugiData"/>
</template>

<style lang="scss">
    @import "bootstrap/scss/bootstrap";
    
</style>
