<template>
  <div>
    <select v-model="selected" @change="selectCountry">
      <option value="0">Select Country</option>
      <option v-for:="country in countries" v-bind:value="country.ID">
        {{ country.Country }}
      </option>
    </select>
    <button @click="onClick" v-show="showBtn">Clear</button>
  </div>
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
      if (this.selected != 0) {
        const selectedCountry = this.countries.find(
          (country) => this.selected === country.ID
        );
        console.log(selectedCountry);
        this.$emit("get-country", selectedCountry);
      }
    },
    onClick() {
      this.$emit("clear");
    },
  },
  computed: {
    showBtn: function () {
      return this.selected != 0;
    },
  },
};
</script>
<style scoped>
div {
  display: flex;
  gap: 1rem;
  margin-bottom: 2rem;
}
select {
  width: 100%;
  border-radius: 1rem;
  padding: 1rem;
  background-color: #eeece8;
  border: 1px solid #344e41;
}
button {
  padding: 1rem 4rem;
  border-radius: 1rem;
  border: 1px solid #344e41;
  background-color: #eeece8;
  transition: background-color 0.3s, color 0.3s;
}
button:hover {
  cursor: pointer;
  background-color: #344e41;
  color: #d4cfc4;
}
</style>