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
        searchCardsByArchetype(){
            axios.get(this.store.yugiohUrl, {
                params: {
                    archetype: this.store.searchArchetype
                }
            })
            .then((response)=>{
                console.log(response.data.data);
                this.store.yugiohCards = response.data.data
            })
        },
        
        getAllCards(){
            axios.get(this.store.yugiohUrl)
            .then((response)=>{
                console.log(response.data.data);
                this.store.yugiohCards = response.data.data
            })
        },
        
        getAllArchetypes(){
            axios.get(this.store.archetypeUrl)
            .then((response)=>{
            console.log(response.data);
            this.store.archetype = response.data;
        })
        },
    },
    created(){
        this.getAllCards();
        this.getAllArchetypes();
    }
}
</script>

<template>

    <AppHeader />

    <AppMain :store.yugiohCard ="elem"  @searched="searchCardsByArchetype()"/>

    <AppFooter />
</template>

<style lang="scss">
@use "assets/scss/main" as *;
@import "assets/scss/partials/reset";
</style>
