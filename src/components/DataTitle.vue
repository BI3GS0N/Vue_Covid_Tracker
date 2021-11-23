<template>
  <div>
    <h2 class="data__title">{{ text }}</h2>
    <p class="data__date">{{ dateConverted }}</p>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "DataTitle",
  props: ["text", "date"],
  computed: {
    dateConverted: function () {
      return moment(this.date).format("DD-MM-YYYY | HH:mm:ss ");
    },
  },
};
</script>

<style scoped>
div {
  text-align: center;
  color: #3a5a40;
  margin-bottom: 2rem;
}
h2 {
  margin-bottom: 1rem;
}
</style>``