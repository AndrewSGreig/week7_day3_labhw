<template lang="html">
<div v-if='country'>
  <p> In the country detail </p>

    <h3>{{ country.name}} </h3>
    <p>Capital: {{ country.capital }} </p>
    <p>Population: {{ country.population }} </p>

  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props:['country']
}
</script>

<style lang="css" scoped>
  div{
    position:fixed;
    top: 20px;
    right: 20px;
  }
</style>
