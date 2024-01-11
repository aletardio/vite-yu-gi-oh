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

      let apiUrl = this.store.endpoint;
      console.log(this.store.endpoint);

      if(this.store.type !== '') {
        apiUrl += `&archetype=${this.store.type}`;
      }

      console.log(this.store.endpoint);

        axios.get(apiUrl).then((response) => {
            this.store.loading = true;
            console.log(response.data.data);
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
