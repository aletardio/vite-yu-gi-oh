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
                <div class="box-cards" v-for="card in store.cards" :key="card.id">
                    <div class="cards">
                        <img :src="card.card_images[0].image_url" :alt="card.name" />
                        <div class="text-cards">{{ card.name }}</div>
                        <div class="type-cards">{{ card.race }}</div>
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
    }

    .box-cards {
        width: calc(100% / 5 - 20px);
        margin: 10px;
        .cards {
            margin: 10px;
            background-color: #D48F38;
    
            img {
                width: 200px;
            }

            .text-cards {
                text-align: center;
                padding: 10px 0;
                color: #fff;
                width: 100%;
                font-weight: 700;
                font-size: 11px;
                text-transform: uppercase;
            }

            .type-cards {
                text-align: center;
                padding: 10px 0;
                font-size: 12px;
            }
        }

    }

</style>