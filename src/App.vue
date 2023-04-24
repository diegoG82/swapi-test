
<script>
import axios from 'axios';
import { store } from './store';
import AppHeader from './components/AppHeader.vue';
import Cardlist from './components/CardList.vue';
import AppSearch from './components/AppSearch.vue';


export default {
  name: 'App',

  components: {
    AppHeader,
    Cardlist,
    AppSearch,

  },

  data() {
    return {
      store,
    };
  },
  mounted() {

    this.getPeople();
  },
  methods: {
    getPeople() {
      this.store.isLoading = true;
      const params = {}
      if (this.store.searchText) {
        console.log(this.store.searchText);
        params.search = this.store.searchText;
      }
      // chiamata axios
      axios.get(this.store.apiURL, {
        params,


      })
        // dato di ritorno dal server
        .then(resp => {
          console.log(resp.data);
          this.store.people = resp.data.results;
        }).catch(err => console.log(err))
        // poi un .finally con arrow function per interrompere isloading
        .finally(() => {
          this.store.isLoading = false;
        });
    }
  }

}


</script>



<template>
  <AppHeader />
  <AppSearch @search="getPeople" />
  <Cardlist />
</template>



<style scoped></style>
