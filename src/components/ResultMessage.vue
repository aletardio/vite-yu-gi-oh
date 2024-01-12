<script>
import { store } from '../store.js';

export default {
    name:'ResultMessage',
    data() {
        return {
            store
        }
    },
    computed:{
        cardsNumber(){
            return store.cards.length;
        }
    }
}
</script>
<template lang="">
    <div class="container bg-black">
        <div class="row">
            <div v-if="store.cards.length > 0"> Found {{cardsNumber}} cards </div>
            <div v-else> Founded 0 cards</div>
        </div>
    </div>
</template>
<style lang="scss" scoped>
    .container.bg-black {
        background-color: #000;
        color: white;
        padding: 10px;
    }
</style>