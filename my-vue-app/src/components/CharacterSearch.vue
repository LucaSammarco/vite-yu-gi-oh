<script>

import { store } from '../store.js'

export default {
    data() {
        return {
            store,

            
        };
    },


    methods: {

        selectArchetype(item){
            store.selectedArchetypes = item;
            console.log(store.selectedArchetypes)
        }
    }
};
</script>

<template>
    <div class="search-contaier">
        
       

                           
                                


                                <button class="btn btn-outline-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">Select Archetype</button>


                                <ul class="dropdown-menu dropdown-menu-end my-dropdown">
                                    
          
                                    

                                    <li> <a href="#" v-for="(item, index) in store.archetypes" :key="index" class=" dropdown-item" @click="selectArchetype(item)">  
                                        
                                        {{ item.archetype_name }}

                                    </a>

                                    </li>


                                </ul>


                
            
       
      
        
    </div>
</template>

<style lang="scss" scoped>

@use '../styles/partial/variables' as *;
 

button {
    margin: 2rem 0 0 7rem;
    background-color: white;
}


.my-dropdown{

    height: 50%;
    overflow-y: scroll;
}
</style>