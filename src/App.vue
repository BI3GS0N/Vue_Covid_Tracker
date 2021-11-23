<template>
  <Header />
  <div class="container">
    <router-view />
  </div>
</template>
<script>
import Header from "@/components/Header.vue";

export default {
  components: {
    Header,
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@100;300;400;700;900&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  font-size: 62.5%;
}
body {
  font-family: "Lato", sans-serif;
  font-size: 1.6rem;
  background-color: #eeece8;
}
.container {
  padding: 2rem;
  display: flex;
  align-content: center;
  justify-content: center;
}
</style>
