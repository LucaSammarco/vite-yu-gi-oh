<script>
import CharacterSearch from './CharacterSearch.vue';
import CharacterList from './CharacterList.vue';
import axios from 'axios';
import { store } from '../store.js'

export default {
    components: {
        CharacterSearch,
        CharacterList
    },
    data() {
        return {
            store
        };
    },
    methods:{
        getCharacters(){

            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10000&offset=0')
                .then((response) =>  {
                    // handle success
                    console.log(response.data.data);
                    this.store.characters = response.data.data;
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                })
                .finally(function () {
                    // always executed
                });

        },

        getArchetype(){

                axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
                    .then((response) =>  {
                        // handle success
                        console.log(response.data);
                        this.store.archetypes = response.data;
                    })
                    .catch(function (error) {
                        // handle error
                        console.log(error);
                    })
                    .finally(function () {
                        // always executed
                    });

                },




        info(){
            console.log('clicked')
            
        }


       
    },
    created(){
            this.getCharacters();
            this.getArchetype();
        }
};
</script>


<template>
    <main>
        
        <CharacterSearch @searched="info"/>
        <CharacterList  />
    </main>
</template>


<style lang="scss" scoped>
@use '../styles/partial/variables' as *;


main {
    
    background-color: $orange;
    height: 100%;
}

</style>