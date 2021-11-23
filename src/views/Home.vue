<template>
  <div v-if="!loading">
    <DataTitle :text="dataTitle" :date="dataDate" />
    <SelectCountry :countries="countries" @get-country="getCountryData" />
    <DataBoxes :stats="dataStats" />
  </div>
  <div class="loading" v-else>
    Loading data
    <i class="fas fa-spinner fa-spin fa-4x"></i>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

import DataTitle from "@/components/DataTitle.vue";
import DataBoxes from "@/components/DataBoxes.vue";
import SelectCountry from "@/components/SelectCountry.vue";

export default {
  name: "Home",
  components: {
    DataTitle,
    DataBoxes,
    SelectCountry,
  },
  data() {
    return {
      dataTitle: "Global",
      dataDate: "",
      dataStats: {},
      countries: [],
      loading: true,
    };
  },
  methods: {
    async fetchData() {
      const res = await axios.get("https://api.covid19api.com/summary");
      const data = await res.data;
      return data;
    },
    getCountryData(country) {
      this.dataStats = country;
      this.dataTitle = country.Country;
    },
  },
  async created() {
    this.loading = true;
    const data = await this.fetchData();
    console.log(data);
    this.dataDate = data.Date;
    this.dataStats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
<style scoped>
.loading {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: 3rem;
}
</style>