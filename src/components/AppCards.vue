<script>

import axios from 'axios';
import { store } from '../store.js';

export default {
    name: 'AppCards',
data() {
    return {
        store
    }
},
methods: {
    getCardsList(){
        axios.get(this.store.endpoint).then((response) => {
            console.log(response.data.data);
            this.store.cards = response.data.data;
        })
    }
},
created() {
    this.getCardsList();
}
}
</script>
<template lang="">
    <div>
        <div class="container">
            <div class="row">
                <div class="col-12" v-for="card, index in store.cards :key="index">
                    <div class="cards">
                        <img :src="" alt="">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
@use '../styles/generals.scss' as *;
@use '../styles/partials/variables' as *;

    .container {
        background-color: #fff;
        height: 400px;
    }
</style>