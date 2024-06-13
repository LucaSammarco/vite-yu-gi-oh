<script>

import CharacterCard from './CharacterCard.vue'
import { store } from '../store.js'

export default {
    data() {
        return {store};
    },

    components: {
        
    },

  computed: {
    filteredCharacters() {
        return store.characters.filter(card => {
            if (store.selectedArchetypes && store.selectedArchetypes.archetype_name != "") {
                return card.archetype === store.selectedArchetypes.archetype_name;
            }
            return true; 
        });
    }
}

    
    
};
</script>

<template>
    
    <div class="container mt-5">

        <h2 class="text-center mb-4">Found {{ filteredCharacters.length }} cards</h2>
        <div class="card-container">
            <div class="card" v-for="(character, index) in filteredCharacters" :key="character.id">

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

@use '../styles/partial/variables' as *;

.container {
    width: 100%;
   
    padding: 1rem;
    background: white;
    margin-top: 1rem;
    
}

.card-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}

.card {
    background-color: $orange;
    border: none;
    width: calc(100% / 6 - 20px);
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
    color: black;
    text-transform: uppercase;
}
</style>
