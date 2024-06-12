<script>

import CharacterCard from './CharacterCard.vue'


export default {
    data() {
        return {};
    },

    components: {
        CharacterCard
    },

    props: {
        characters: {
            type: Array,
            required: true
        }
    }
};
</script>

<template>
    
    <div class="container mt-5">
        <h2 class="text-center mb-4">Found {{ characters.length }} cards</h2>
        <div class="card-container">
            <div class="card" v-for="(character, index) in characters" :key="character.id">
                <img :src="character.card_images[0].image_url" :alt="character.name" class="card-img-top">
                <div class="card-body">
                    <h5 class="card-title"> {{ character.name }}</h5>
                    <p class="card-text"> {{ character.archetype }} </p>
                </div>
            </div>
        </div>
    </div>

</template>


<style lang="scss" scoped>
.container {
    width: 100%;
   
    margin-left: auto;
    margin-right: auto;
    padding: 1rem;
}

.card-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.card {
    background-color: #D4A017;
    border: none;
    width: calc(100% / 5 - 20px);
    margin: 10px;
    text-align: center;
}

.card-img-top {
    width: 100%;
    height: auto;
}

.card-title {
    font-size: 1rem;
    color: #ffffff;
    text-transform: uppercase;
}

.card-text {
    color: #ffffff;
    text-transform: uppercase;
}
</style>
