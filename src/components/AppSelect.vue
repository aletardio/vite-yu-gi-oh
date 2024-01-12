<script>

import axios from 'axios';
import { store } from '../store.js';

export default {
    name:'AppSelect',
data(){
        return {
            store, 
            typeCards: [],
        }
},
created() {
    this.getArchetypesList()
},
methods:{
    getArchetypesList(){
        axios.get(store.apiArchetypeUrl).then((response) => {
            this.typeCards = response.data.slice(10,35);
        })
    }
}
}
</script>
<template lang="">
    <div>
        <div class="container">
            <div class="row">
                <div class="col-12">
                    <label for="filter" class="control-label">Type</label>
                    <select class="form-select" id="filter" v-model="this.store.type" @change="$emit('type_selected')">
                        <option :value="archetype.archetype_name" v-for="archetype, index in typeCards" :key="index">{{ archetype.archetype_name}}</option>
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