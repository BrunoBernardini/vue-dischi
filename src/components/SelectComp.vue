<template>
  <select class="form-select" @change="sendFilters" v-model="selectedFilter">
    <option selected value="">
      <span v-if="filterParameters.filterName===''">Seleziona un {{type}}</span>
      <span v-else>Deseleziona</span></option>
    <option
      v-for="(option, index) in options"
      :key="`${option}-${index}`"
      :value="option">{{option}}</option>
  </select>
</template>

<script>

export default {
  name: "SelectComp",
  props: {
    options: Array,
    type: String
  },
  data(){
    return{
      filterParameters: {
        filterType: this.type,
        filterName: ""
      },
      selectedFilter: ""
    }
  },
  methods: {
    sendFilters(filterOption){
      this.filterParameters.filterName = filterOption.target.value;
      this.$emit("sendFilterToHeader", this.filterParameters);
    }
  }
}
</script>

<style lang="scss" scoped>
select{
  max-width: 193px;
}
</style>