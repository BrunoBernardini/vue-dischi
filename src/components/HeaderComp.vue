<template>
  <header>
    <img src="../assets/img/logo.svg" alt="">
    <div class="select-container">
      <SelectComp 
        :options="filters.authors"
        type="autore"
        @sendFilterToHeader='sendFilterToApp'/>
      <SelectComp
        :options="filters.genres"
        type="genere"
        @sendFilterToHeader='sendFilterToApp'/>
    </div>
  </header>
</template>

<script>
import SelectComp from './SelectComp.vue';
export default {
  name: "HeaderComp",
  components: {
    SelectComp
  },
  props:{
    filters: Object
  },
  methods:{
    sendFilterToApp(filterObject){
      this.$emit("sendFilterToApp", filterObject);
    }
  }
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
  margin-bottom: 65px;
  height: 69px;
  background-color: $secondary-color;
  img{
    width: 38px;
    filter: invert(48%) sepia(71%) saturate(448%) hue-rotate(84deg) brightness(95%) contrast(91%);
  }
  .select-container{
    display: flex;
    justify-content: space-between;
    width: 420px;
  }
}
</style>