<template>
  <div class="container">
      <div v-for="(type,index) in types" :key="index">
        <div class="types" v-bind:class="type">{{type}}</div>
        <div v-for="(pokemon,index) in pokemons" :key="index" class="pokemon">
          <div v-if="pokemon.types[0] === type ||pokemon.types[1] === type">
            <table>
              <tr>
                <th>{{ pokemon.name }}</th>
                <th>{{ pokemon.types[0] }}</th>
                <th>{{ pokemon.types[1] }}</th>
              </tr>
            </table>
          </div>
        </div>
      </div>
  </div>
</template>

<script>
const axios = require('axios');
const url = 'https://raw.githubusercontent.com/kotofurumiya/pokemon_data/master/data/pokemon_data.json';
const param = ['ノーマル','ほのお','みず','でんき','くさ','こおり','かくとう','どく','じめん','ひこう','エスパー','むし','いわ','ゴースト','ドラゴン','あく','はがね','フェアリー']
export default {
  asyncData({ params, error }) {
    return axios
    .get(url)
    .then((res) =>{
      console.log(res)
      return {pokemons: res.data,types:param}
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

table {
  margin: 0 auto;
}

th {
  width: 130px;
  margin: 0;
}

.types {
  width: 399px;
  height: 40px;
  line-height: 40px;
  margin: 0 auto;
  color:#fff;
  font-weight:bold;
}
.ノーマル {
  background-color: rgb(212, 211, 211);
}
.ほのお {
  background-color: rgb(255, 174, 121);;
}

.みず {
  background-color: rgb(121, 213, 255);;
}

.でんき {
  background-color: rgb(219, 221, 103);;
}

.くさ {
  background-color: rgb(159, 255, 121);;
}

.こおり {
  background-color: rgb(121, 195, 255);;
}

.かくとう {
  background-color: rgb(255, 121, 143);;
}

.どく {
  background-color: rgb(233, 121, 255);;
}

.じめん {
  background-color: rgb(255, 181, 121);;
}

.ひこう {
  background-color: rgb(121, 152, 255);;
}

.エスパー {
  background-color: rgb(117, 73, 126);;
}

.むし {
  background-color: rgb(81, 180, 103);;
}

.いわ {
  background-color: rgb(137, 255, 121);;
}

.ゴースト {
  background-color: rgb(74, 17, 128);;
}

.ドラゴン {
  background-color: rgb(235, 124, 50);;
}

.あく {
  background-color: rgb(39, 76, 196);;
}

.はがね {
  background-color: rgb(77, 69, 65);;
}

.フェアリー {
  background-color: rgb(248, 159, 218);;
}


</style>
