<template lang="html">
  <div id='detail' v-if='country'>
    <h3>{{country.name}}</h3>
    <h4>Capital City: {{country.capital}}</h4>
    <h4>Population: {{country.population}}</h4>
    <h4>Languages Spoken: {{country.languages.name}}</h4>
    <img :src="country.flag">
  </div>

</template>

<script>
export default {
  name:'countries-detail',
  props:['country']
}
</script>

<style lang="css" scoped>
h3{
  color: red;
}
#detail{
  color: white;
  border: 4px solid red;
  background-color: blue;
  width:300px;
  position: fixed;
}
img{
  width:300px;
  border-top: 5px solid black;
  border-bottom: 5px solid black;
  padding: 0px;
}
</style>
