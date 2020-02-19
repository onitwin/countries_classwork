<template>
  <div id="app">
    <h1>Countries</h1>
    <div>
      <countries-list :countries="countries"></countries-list>
    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import CountriesList from './components/CountriesList'

export default {
  name: 'app',
  data(){
    return {
      countries:[],
      selectedCountry:null
        //stuff goes here
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res=> res.json())
    .then(countries=>this.countries=countries)
  },
  components:{
    "countries-list":CountriesList
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
