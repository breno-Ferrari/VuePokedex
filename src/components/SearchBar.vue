<template>
  <section class="searchBox">
    <input type="search" id="filter" name="filter" class="filter" placeholder="Search" @input="atualizarTexto" v-model="valor">
  </section>
</template>

<script>
export default {
  data() {
    return {
      valor: ''
    };
  },
  methods: {
    atualizarTexto() {
      this.$emit('atualizarTexto', this.valor);
    }
  }
};
</script>


<style lang="scss" scoped>
.searchBox{
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.filter{
    background-color: $background-search-bar;
    width: $width;
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
