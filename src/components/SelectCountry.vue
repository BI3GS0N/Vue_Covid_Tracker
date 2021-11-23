<template>
  <select v-model="selected" @change="selectCountry">
    <option value="0">Select Country</option>
    <option v-for:="country in countries" v-bind:value="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>
<script>
export default {
  name: "SelectCountry",
  props: {
    countries: Array,
  },
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    selectCountry() {
      console.log(this.selected);
      const selectedCountry = this.countries.find(
        (country) => this.selected === country.ID
      );
      console.log(selectedCountry);

      this.$emit("get-country", selectedCountry);
    },
  },
};
</script>
<style scoped>
select {
  width: 100%;
  border-radius: 1rem;
  padding: 1rem;
  margin-bottom: 2rem;
  background-color: #eeece8;
}
</style>