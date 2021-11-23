<template>
  <div class="wrapper">
    <div class="box box--1">
      <h3 class="box__title">Cases</h3>
      <div class="box__info">
        <h4>
          New: <span>{{ numberWithCommas(stats.NewConfirmed) }}</span>
        </h4>
        <!-- {{ numberWithCommas(stats.NewConfirmed) }} -->
      </div>
      <div class="box__info">
        <h4>
          <!-- Total: <span>{{ numberWithCommas(stats.TotalConfirmed) }}</span> -->
        </h4>
      </div>
    </div>

    <div class="box box--2">
      <h3 class="box__title">Deaths</h3>
      <div class="box__info">
        <h4>
          <!-- New: <span> {{ numberWithCommas(stats.NewDeaths) }}</span> -->
        </h4>
      </div>
      <div class="box__info">
        <h4>
          <!-- Total: <span>{{ numberWithCommas(stats.TotalDeaths) }}</span> -->
        </h4>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBoxes",
  props: ["stats"],
  methods: {
    numberWithCommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>
<style scoped>
.wrapper {
  display: flex;
  gap: 2rem;
  justify-content: center;
  flex-flow: row wrap;
}
.box {
  min-width: 350px;
  text-align: center;
  background-color: #a3b18a;
  border-radius: 1rem;
  padding: 2rem;
  box-shadow: 0px 3px 10px rgba(0, 0, 0, 0.3);
}
.box__title {
  margin-bottom: 1rem;
}
.box--2 {
  background-color: #75875a;
}
.box__info:first-of-type {
  margin-bottom: 0.5rem;
}
span {
  font-weight: 400;
}
</style>