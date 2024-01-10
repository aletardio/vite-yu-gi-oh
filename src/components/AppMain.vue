<script>

import AppCards from './AppCards.vue';

export default {
    name: 'AppMain',
    components:{
        AppCards
    }
}
</script>
<template lang="">
    <main>
        <AppCards />
    </main>
</template>
<style lang="scss" scoped>
@use '../styles/generals.scss' as *;
@use '../styles/partials/variables' as *;
</style>