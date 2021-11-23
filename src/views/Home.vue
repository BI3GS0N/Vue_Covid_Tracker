<template>
  <DataTitle :text="dataTitle" :date="dataDate" />
  <DataBoxes :stats="dataStats" />
</template>

<script>
// @ is an alias to /src
import axios from "axios";

import DataTitle from "@/components/DataTitle.vue";
import DataBoxes from "@/components/DataBoxes.vue";

export default {
  name: "Home",
  components: {
    DataTitle,
    DataBoxes,
  },
  data() {
    return {
      dataTitle: "Global",
      dataDate: "",
      dataStats: {},
    };
  },
  methods: {
    async fetchData() {
      const res = await axios.get("https://api.covid19api.com/summary");
      const data = res.data;
      return data;
    },
  },
  async created() {
    const data = await this.fetchData();
    console.log(data);
    this.dataDate = data.Date;
    this.dataStats = data.Global;
  },
};
</script>
