<script setup>
  import PokemonCard from '../components/PokemonCard.vue'
</script>

<template>
  <section class="pokedexBox">
    <PokemonCard/>
  </section>
</template>

<style lang="scss" scoped>
.pokedexBox{
  @include general-styles;
}
</style>