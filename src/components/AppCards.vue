<script>

import { store } from '../store.js';

export default {
    name: 'AppCards',
data() {
    return {
        store
    }
}
}
</script>
<template lang="">
    <div class="space">
        <div class="container">
            <div class="row">
                <div class="box-cards" v-for="card in this.store.cards" :key="card.id">
                    <div class="cards">
                        <img :src="card.card_images[0].image_url" :alt="card.name" />
                        <div class="text-cards">{{ card.name }}</div>
                        <div class="type-cards">{{ card.archetype }}</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
@use '../styles/generals.scss' as *;
@use '../styles/partials/variables' as *;


    .space {
        padding: 60px 0;
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
    }

</style>