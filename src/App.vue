<script>

import AppHeader from './components/AppHeader.vue';
import AppLoader from './components/AppLoader.vue';
import AppCards from './components/AppCards.vue';
import AppSelect from './components/AppSelect.vue';
import ResultMessage from './components/ResultMessage.vue';

import axios from 'axios';
import { store } from './store.js'
export default {
  components: {
    AppHeader,
    AppLoader,
    AppCards,
    AppSelect,
    ResultMessage
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

      let apiUrl = this.store.endpoint;

      if(this.store.type !== '') {
        apiUrl += `&archetype=${this.store.type}`;
      }

        axios.get(apiUrl).then((response) => {
            this.store.loading = true;
            this.store.cards = response.data.data;
            this.store.loading = false;
        })
    },
  }
}
</script>
<template lang="">
  <div>
    <!-- Loading -->
    <AppLoader v-if="this.store.loading" />
    <div v-else>
      <!-- Header -->
      <AppHeader title="Yu-Gi-Oh Api" />
      <ResultMessage />
      <!-- Type Cards -->
      <AppSelect @type_selected = "getCardsList" />
      <!-- Cards list -->
      <AppCards />
    </div>
  </div>
</template>
<style lang="scss">
@use './styles/generals.scss' as *;
@use './styles/partials/variables' as *;
</style>
