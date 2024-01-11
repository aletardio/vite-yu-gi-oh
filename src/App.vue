<script>

import AppHeader from './components/AppHeader.vue';
import AppLoader from './components/AppLoader.vue';
import AppCards from './components/AppCards.vue';
import AppSelect from './components/AppSelect.vue';

import axios from 'axios';
import { store } from './store.js'
export default {
  components: {
    AppHeader,
    AppLoader,
    AppCards,
    AppSelect
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.getCardsList();
  },
  methods: {
    getCardsList(){
        axios.get(this.store.endpoint).then((response) => {
            console.log(response.data.data);
            this.store.cards = response.data.data;
            store.loading = false;
        })
    }
  }
}
</script>
<template lang="">
  <div>
    <AppLoader v-if="store.loading" />
    <div v-else>
      <AppHeader title="Yu-Gi-Oh Api" />
      <AppSelect />
      <AppCards />
    </div>
  </div>
</template>
<style lang="scss">
@use './styles/generals.scss' as *;
@use './styles/partials/variables' as *;
</style>
