<script>
import CharacterSearch from './CharacterSearch.vue';
import CharacterList from './CharacterList.vue';
import axios from 'axios';

export default {
    components: {
        CharacterSearch,
        CharacterList
    },
    data() {
        return {
            characters: []
        };
    },
    methods:{
        getCharacters(){

            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                .then((response) =>  {
                    // handle success
                    console.log(response.data.data);
                    this.characters = response.data.data;
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                })
                .finally(function () {
                    // always executed
                });

        }

       
    },
    created(){
            this.getCharacters();
        }
};
</script>


<template>
    <div>
        <h1>Main</h1>
        <!-- <CharacterSearch /> -->
        <CharacterList :characters="characters" />
    </div>
</template>


<style lang="scss" scoped>

</style>