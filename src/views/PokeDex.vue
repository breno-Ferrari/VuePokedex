<script setup>
  import PokemonCard from '../components/PokemonCard.vue'
  import SearchBar from '../components/SearchBar.vue'

</script>

<script>
export default {
  data() {
    return {
      textoBusca: ''
    };
  },
  methods: {
    lidarComTextoAtualizado(texto) {
      this.textoBusca = texto;
      console.log(this.textoBusca);
    }
  }
};
</script>

<template>
   <SearchBar @atualizarTexto="lidarComTextoAtualizado" />
  <section class="pokedexBox">
    <PokemonCard :textoBusca="textoBusca"/>
  </section>
</template>

<style lang="scss" scoped>
.pokedexBox{
  @include general-styles;
}
</style>