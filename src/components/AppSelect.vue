<script>


import { store } from '../store.js';

export default {
    name:'AppSelect',
data(){
        return {
            store, 
            typeCards: [
            'Neos',
            'Armed Dragon',
            'Chaos Phantom',
            'Sacred Beast',
            'Inzektor'
        ]
        }
},
}
</script>
<template lang="">
    <div>
        <div class="container">
            <div class="row">
                <div class="col-12">
                    <label for="filter" class="control-label">Type</label>
                    <select class="form-select" id="filter" v-model="this.store.type" @change="$emit('type_selected')">
                        <option value="" selected>Select type</option>
                        <option v-for="type, index in typeCards" :key="index" :value="type">
                            {{ type }}
                        </option>
                    </select>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
    .control-label {
        font-weight: 600;
        padding-top: 40px;
        padding-right: 15px;

    }
    .form-select {
        width: 15%;
         margin-top: 10px;
    }
</style>