<template>
  <div id="app">
    <TheHeader />
    <div class="router-box">
      <transition name="slide-fade" mode="out-in">
        <router-view />
      </transition>
    </div>
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader";
export default {
  components: {
    TheHeader,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Montserrat&display=swap");
#app {
  font-family: montserrat, sans-serif;
  background: black;
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
  min-height: 100vh;
  width: 100%;
  font-size: 12px;
  overflow-x: hidden;
  scrollbar-width: none;
  font-family: montserrat, sans-serif;
}

.router-box {
  height: calc(100% - 90px);
  width: 100%;
  padding-top: 90px;
  font-family: montserrat, sans-serif;
  scrollbar-width: none;
  overflow-x: hidden;
}

/* Enter and leave animations can use different */
/* durations and timing functions.              */
.slide-fade-enter-active {
  transition: all 1s cubic-bezier(0.165, 0.84, 0.44, 1);
}
.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(0.165, 0.84, 0.44, 1);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(-10px);
  opacity: 0;
}
</style>
