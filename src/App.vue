<script>

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

import axios from 'axios';
import { store } from './store.js'
export default {
  components: {
    AppHeader,
    AppMain
  },
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
    <AppHeader title="Yu-Gi-Oh Api" />
    <AppMain />
  </div>
</template>
<style lang="scss">
@use './styles/generals.scss' as *;
@use './styles/partials/variables' as *;
</style>
