<script>
export default {
    data() {
        return {
            
        };
    },
    methods: {

    },
    props: {
        card: Object
    }
}
</script>
<template>
<div class="col-2 text-black me-4 my-3  bg-success text-center">
    <div class="img-container">
        <img :src="card.card_images[0].image_url" alt="">
    </div>
    <h3 class="text-center">
        {{ card.name }}
    </h3>
    <h5 class="text-center">
        {{ card.archetype }}
    </h5>
</div>
</template>
<style lang="scss" scoped>

.img-container{
    height: 200px;
    width: 100%;

    img{
        width: 100%;
        height: 100%;
    }
}
</style>