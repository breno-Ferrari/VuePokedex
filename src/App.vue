<script setup>
  import PokeDex from './views/PokeDex.vue';
</script>


<template>
  <main class="alignDivs">
    <PokeDex/>
  </main>
</template>

<style lang="scss" scoped>
  .alignDivs{
    @include general-styles;
  }
</style>