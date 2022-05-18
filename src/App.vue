<template>
  <div id="app">
    <HeaderComp
      :filters="filters"
      @sendFilterToApp='setFilterToMain'/>
    <MainComp
      :currentFilters="currentFilters"
      @transferFilters='getFilters'/>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },
  data(){
    return{
      filters: {},
      currentFilters: {
        genre: "",
        author: ""
      }
    }
  },
  methods:{
    getFilters(sentFilters){
      this.filters = sentFilters;
    },
    setFilterToMain(filterObject){
      if(filterObject.filterType === "genere"){
        this.currentFilters.genre = filterObject.filterName;
      }
      else if(filterObject.filterType === "autore"){
        this.currentFilters.author = filterObject.filterName;
      }
    }
  }
}
</script>

<style lang="scss">
@import "./assets/style/vars";
@import "./assets/style/general";
#app {
  min-height: 100vh;
}
</style>
