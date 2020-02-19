<template>
  <div id="app">
    <h1>Countries</h1>
    <div>
      <countries-detail :country="selectedCountry"></countries-detail>
      <countries-list :countries="countries"></countries-list>

    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import CountriesList from './components/CountriesList.vue';
import CountriesDetail from './components/CountriesDetail.vue';

export default {
  name: 'app',
  data(){
    return {
      countries:[],
      selectedCountry:null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res=> res.json())
    .then(countries=>this.countries=countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components:{
    "countries-list":CountriesList,
    "countries-detail":CountriesDetail
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
