<script>

import { store } from '../store.js'

export default {
    data() {
        return {
            store
        };
    }
};
</script>

<template>
    <div class="search-contaier">
        
        <div class="row">
            <div class="col-">

                            <div class="form-floating">
                            <div class="input-group mb-3">

                                    <input type="text" class="form-control" placeholder="Recipient's username" aria-label="Recipient's username" aria-describedby="button-addon2" v-model="store.searchedText">

                                    <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="$emit('searched')">Button</button>
                                    </div>
                            </div>
            
            </div>
        </div>
        
    </div>
</template>

<style lang="scss" scoped>

</style>