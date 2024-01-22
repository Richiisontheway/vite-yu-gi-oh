<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';
import { store } from '../src/store'
export default {
    data() {
        return {
            yugiohUrl: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',
            store,
        };
    },
    components: {
        AppHeader,
        AppMain,
        AppFooter,
    },  
    methods: {

    },
    mounted(){
        axios.get(this.yugiohUrl)
        .then((response)=>{
            console.log(response.data.data);
            this.store.yugiohCard = response.data.data
        })
    }
}
</script>

<template>

    <AppHeader />

    <AppMain :store.yugiohCard ="elem" />

    <AppFooter />
</template>

<style lang="scss">
@use "assets/scss/main" as *;
@import "assets/scss/partials/reset";
</style>
