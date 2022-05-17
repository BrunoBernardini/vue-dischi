<template>
  <div class="disc-card">
    <img :src="cardInfo.poster" :alt="`Title: ${cardInfo.title}; Genre: ${cardInfo.genre}`">
    <h4>{{cardInfo.title}}</h4>
    <span class="author">{{cardInfo.author}}</span>
    <span class="year">{{cardInfo.year}}</span>
  </div>
</template>

<script>
export default {
  name: "CardItem",
  props: {
    cardInfo: Object
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars";
@import "../assets/style/general";
.disc-card{
  display: flex;
  flex-direction: column;
  width: 227px;
  height: 378px;
  margin: 0 16px 10px 16px;
  margin-bottom: 32px;
  background-color: $secondary-color;
  padding: 16px;
  text-align: center;
  img{
    margin-bottom: 18px;
  }
  h4{
    color: white;
    font-size: 1rem;
    margin-bottom: 19px;
  }
  span{
    color: gray;
  }
  .author{
    font-size: 20px;
  }
}
</style>