<template>
  <main class="container main-container">
    <div v-if="isLoaded" class="cards-container">
      <CardItem
      v-for="(card, index) in filteredCards"
      :key="`card-${index}`"
      :cardInfo="card"/>
    </div>
    <div v-else class="loader-container">
      <LoaderComp/>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import CardItem from "./CardItem.vue";
import LoaderComp from "./LoaderComp.vue";

export default {
  name: "MainComp",
  components: {
    CardItem,
    LoaderComp
  },
  props: {
    currentFilters: Object
  },
  data(){
    return{
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      cards: [],
      isLoaded: false,
      filters: {
        genres: [],
        authors: []
      }
    }
  },
  mounted(){
    this.getApi();
  },
  methods: {
    getApi(){
      axios.get(this.apiUrl)
        .then(resp=>{
          this.cards = resp.data.response;
          this.getGenres();
          this.getAuthors();
          this.$emit('transferFilters', this.filters)
          this.isLoaded = true;
        })
        .catch(error=>{
          console.log(error);
        })
    },
    getGenres(){
      for(let card of this.cards){
        if(!this.filters.genres.includes(card.genre)) this.filters.genres.push(card.genre)
      }
    },
    getAuthors(){
      for(let card of this.cards){
        if(!this.filters.authors.includes(card.author)) this.filters.authors.push(card.author)
      }
    },
  },
  computed:{
    filteredCards(){
      let filteredArray = [];
      if(this.currentFilters.genre != ""){
        filteredArray = this.cards.filter(card=>{
          return card.genre===this.currentFilters.genre;
        })
      }
      else filteredArray = this.cards;
      if(this.currentFilters.author != ""){
        filteredArray = filteredArray.filter(card=>{
          return card.author===this.currentFilters.author;
        })
      }
      return filteredArray;
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars";
@import "../assets/style/general";
.main-container{
  padding: 0;
}
.cards-container{
  display: flex;
  width: 100%;
  justify-content: center;
  flex-wrap: wrap;
}
.loader-container{
  display: flex;
  height: 50vh;
  justify-content: center;
  align-items: center;
}
</style>