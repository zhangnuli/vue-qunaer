<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list :cities="cities" :hot="hot" :letter="letter"></city-list>
    <city-alpahbet :cities="cities" @change="handChange"></city-alpahbet>
  </div>
</template>
<script>
import axios from "axios";
import CityHeader from "./compoents/Header";
import CitySearch from "./compoents/Search";
import CityList from "./compoents/List";
import CityAlpahbet from "./compoents/Alpahbet";
export default {
  data() {
    return {
      cities: {},
      hot: [],
      letter:''
    };
  },
  methods: {
    getCityInfo() {
      axios.get("api/city.json").then(this.getCityInfoSucc);
    },
    getCityInfoSucc(res) {
      res = res.data;
      if (res.ret && res.data) {
        let data = res.data;
        this.cities = data.cities;
        this.hot = data.hotCities;
      }
    },
    handChange(letter){
      this.letter=letter;
    }
  },
  mounted() {
    this.getCityInfo();
  },
  computed: {},
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlpahbet
  }
};
</script>
<style scoped>

</style>
