<template>
  <div class="container">
    <div v-for="(pokemon,index) in pokemons" :key="index" class="pokemon">
      <div>
        {{ pokemon.name }}
        {{ pokemon.types[0] }}
        {{ pokemon.types[1] }}
      </div>
    </div>
  </div>
</template>

<script>
const axios = require('axios');
const url = 'https://raw.githubusercontent.com/kotofurumiya/pokemon_data/master/data/pokemon_data.json';
export default {
  asyncData({ params, error }) {
    return axios
    .get(url)
    .then((res) =>{
      console.log(res)
      return {pokemons: res.data}
    })
    .catch((e) => {
      error({pokemon:e.ressponse.status,message:'ERROR'})
    })
  }
}
</script>

<style>
.container {
  margin: 50px auto;
  text-align:center;
}

</style>
