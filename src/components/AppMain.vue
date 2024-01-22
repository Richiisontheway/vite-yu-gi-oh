<script>
import { store } from '../store';
import singolCard from './singolCard.vue';
export default {
    data() {
        return {
            store,
        };
    },
    components : {
        singolCard
    },
    methods: {

    },
}
</script>

<template>
    <main class="bg-warning">
        <div class="container">
            <form class="py-4">
                <select>
                <option selected>Alien</option>
                </select>
            </form>
            <div class="bg-light-subtle p-4">
                <section class="bg-dark text-light p-2 fw-bold container">
                    Founded n° card
                </section>
                <section class="container">
                    <div class="row">
                        <singolCard 
                        v-for="(elem, i) in store.yugiohCard" 
                        :key="i"
                        :card="elem"/>
                    </div>
                </section>
            </div>
        </div>
        
    </main>
</template>

<style lang="scss">

</style>
