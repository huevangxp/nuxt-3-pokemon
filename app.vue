<template>
  <div>
    <h1>huevang love progammer {{love}}</h1>
    <div>
    <div v-for="(item, index) in result" :key="index">
      <!-- <img :src="`http://pokeapi.co/media/sprites/pokemon/${item.name}.png`"/> -->
      <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${index + 1}.png`" />
      <h1>{{item.name}}</h1>
    </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      love: 'huevnag',
      result: []
    }
  },
  mounted() {
    this.getData();
  },
  methods: {
   async getData(){
       await axios.get('https://pokeapi.co/api/v2/pokemon?limit=100000&offset=0').then((res)=>{
        const data = res.data.results;
        this.result = data;
       })
   
    }
  },
}
</script>