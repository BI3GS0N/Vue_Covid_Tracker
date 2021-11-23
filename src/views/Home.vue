<template>
  <DataTitle :text="dataTitle" :date="dataDate" />
</template>

<script>
// @ is an alias to /src
import DataTitle from "@/components/DataTitle.vue";
import axios from "axios";
export default {
  name: "Home",
  components: {
    DataTitle,
  },
  data() {
    return {
      dataTitle: "Global",
      dataDate: "",
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
  },
};
</script>
