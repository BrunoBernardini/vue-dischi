<template>
  <main class="container main-container">
    <div v-if="isLoaded" class="cards-container">
      <CardItem
      v-for="(card, index) in cards"
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
  data(){
    return{
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      cards: [],
      isLoaded: false
    }
  },
  mounted(){
    this.getApi();
  },
  methods: {
    getApi(){
      axios.get(this.apiUrl)
        .then(resp=>{
          console.log(resp.data);
          this.cards = resp.data.response;
          this.isLoaded = true;
        })
        .catch(error=>{
          console.log(error);
        })
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