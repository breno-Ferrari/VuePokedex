
<script>
  import PokemonCard from '../components/PokemonCard.vue';
  import SearchBar from '../components/SearchBar.vue';
  export default {
    components:{
      PokemonCard,
      SearchBar
    },
  };
</script>

<template>
   <SearchBar/>
  <section class="pokedexBox">
    <PokemonCard/>
  </section>
</template>

<style lang="scss" scoped>
.pokedexBox{
  @include general-styles;
}
</style>