<template>
  <header>
    <img src="../assets/img/logo.svg" alt="">
    <select class="form-select top-select">
      <option selected>Seleziona un genere</option>
      <option value="1">Uno</option>
      <option value="2">Due</option>
      <option value="3">Tre</option>
    </select>
  </header>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars";
@import "../assets/style/general";
header{
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 25px;
  height: 69px;
  background-color: $secondary-color;
  img{
    width: 38px;
    filter: invert(48%) sepia(71%) saturate(448%) hue-rotate(84deg) brightness(95%) contrast(91%);
  }
  .top-select{
    max-width: 193px;
  }
}
</style>