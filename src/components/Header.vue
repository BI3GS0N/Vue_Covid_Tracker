<template>
  <header>
    <i class="fas fa-virus fa-5x"></i>
    <div class="info">
      <h1 class="header__title">Covid Tracker</h1>
      <p class="header__description">by <a href="#">Sylwester Biega</a></p>
    </div>
    <i class="fas fa-virus fa-5x"></i>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
header {
  text-align: center;
  background-color: #588157;
  color: #a3b18a;
  padding: 2rem;
  margin-bottom: 2rem;
  display: flex;
  justify-content: space-between;
}
h1 {
  font-size: 4rem;
}
a {
  text-decoration: none;
  color: #000;
}
</style>