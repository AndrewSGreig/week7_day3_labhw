<template>
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <countries-list :countries='countries'></countries-list>
      <!-- <p> {{countries}} </p> -->
      <country-detail :country='selectedCountry'></country-detail>
    </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue';
import { eventBus } from './main.js';
import CountryDetail from './components/CountryDetail.vue';


export default {
  // name: 'App',
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },

  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
  //console.log('within $on', country);
   this.selectedCountry = country;
});


  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail

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
