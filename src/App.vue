<template>
  <div id="app">
    <TheHeader />
    <div class="router-box">
      <router-view />
    </div>
    <TheKontakt />
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader";
import TheKontakt from "./components/TheKontakt";
export default {
  components: {
    TheHeader,
    TheKontakt,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Montserrat&display=swap");
#app {
  font-family: montserrat, sans-serif;
}
*,
*::after,
*::before {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body,
html {
  min-height: 100vh; //settes til min-height
  width: 100%;
  font-size: 12px;
  overflow-x: hidden;
}

.router-box {
  height: 100%;
  width: 100%;
  padding-top: 90px;
}
</style>
