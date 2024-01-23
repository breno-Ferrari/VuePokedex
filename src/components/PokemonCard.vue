<script>
  import axios from 'axios';
  export default {
    data() {
      return {
        apiData: null,
        pokemonDetailsList: [],
        filteredPokemonList: [],
        textoBusca:""
      };
    },
    methods: {
      async getPokemon() {
        try {
          const response = await axios.get('https://pokeapi.co/api/v2/pokemon?limit=151');
          this.apiData = response.data;

          const requests = this.apiData.results.map((_, index) => 
            axios.get(`https://pokeapi.co/api/v2/pokemon/${index + 1}/`)
          );


          const responses = await axios.all(requests);

          this.pokemonDetailsList = responses.map((response) => response.data);
          this.filteredPokemonList = [...this.pokemonDetailsList];
        } catch (error) {
          console.error('Erro ao obter dados da API', error);
        }
      },
    },
    beforeMount() {
      this.getPokemon();
    },
    computed:{
      PokemonList(){
        document.querySelector("#filter").addEventListener("input",(e)=>{
          this.textoBusca = e.target.value
        })
        if(this.textoBusca.trim().length > 0){
          return this.filteredPokemonList.filter((pokemon)=> pokemon.name.toLowerCase().includes(this.textoBusca.toLowerCase().trim()) )
        }
        return this.filteredPokemonList;
      }
    }
  };
</script>

<template>
  <div v-if="apiData && apiData.results" class="align" >
    <div class="body" v-for="(pokemon, index) in PokemonList" :key="index" @atualizarTexto="lidarComTextoAtualizado" :textoBusca="textoBusca">
      <div class="image">
        <img :src="pokemon.sprites.front_default" alt="{{pokemon.name}}" >
      </div>
      <div class="texts">
          <p> {{ pokemon.name }} </p>
          <p> #{{ pokemon.id }} </p>
      </div>
    </div>
  </div>
</template>



<style lang="scss" scoped>
.align{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 1rem;
    width: $inner-width;
  .body{
    background-color: $card-color;
    width: 15rem;
    padding: 0.5rem;
    .image{
      display: flex;
      align-items: center;
      justify-content: center;
      img{
        object-fit: contain;
      }    
    }
    .texts{
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
    }
  }
}
.searchBox{
 @include general-styles;
}
.filter{
    background-color: $background-search-bar;
    width: $inner-width;
    height: 3rem;
    border: none;
    border-bottom:0.1rem solid #A6A6A6;
    color: #A6A6A6;
    &:hover,&:focus{
      outline: none;
      color: #2b2b2b;
      border-bottom:0.1rem solid #2b2b2b;
    }
  }
</style>



