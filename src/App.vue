<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';
import { store } from '../src/store'
export default {
    data() {
        return {
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
        axios.get(store.yugiohUrl)
        .then((response)=>{
            console.log(response.data.data);
            this.store.yugiohCard = response.data.data
        })
        axios.get(store.archetypeUrl)
        .then((response)=>{
            console.log(response.data);
            this.store.archetypeUrl = response.data
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
