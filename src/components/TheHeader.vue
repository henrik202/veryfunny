<template>
  <header class="header-wrapper">
    <nav class="header-nav">
      <!--grid container-->
      <div class="header-logo">
        <router-link class="logo-link" to="/">
          <img
            src="~@/assets/Lofothval_sort.png"
            alt="lofothval logo"
            id="lfw-logo"
          />
        </router-link>
      </div>
      <ul class="nav-links">
        <b-nav tabs justified id="lg-links">
          <b-nav-item :to="{ name: 'Oppskrifter' }">Oppskrifter</b-nav-item>
          <b-nav-item :to="{ name: 'Hvalfangst' }">Hvalfangst</b-nav-item>
          <b-nav-item :to="{ name: 'About' }">Om oss</b-nav-item>
        </b-nav>
        <b-dropdown
          id="dropdown-right"
          right
          text="Meny"
          variant="primary"
          class="m-2"
          size="lg"
        >
          <b-dropdown-item
            :to="{ name: 'Oppskrifter' }"
            href="#"
            style="height: fit-content; width: 500px; font-size: 1.5em"
            >Oppskrifter</b-dropdown-item
          >
          <b-dropdown-item
            :to="{ name: 'Hvalfangst' }"
            href="#"
            style="
              height: fit-content;
              width: 500px;
              font-size: 1.5em;
              margin-top: 20px;
            "
            >Hvalfangst</b-dropdown-item
          >
          <b-dropdown-item
            :to="{ name: 'About' }"
            href="#"
            style="
              height: fit-content;
              width: 500px;
              font-size: 1.5em;
              margin-top: 20px;
            "
            >Om oss</b-dropdown-item
          >
        </b-dropdown>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: "TheHeader",
};
</script>

<style lang="scss" scoped>
.show {
}
.header-wrapper {
  height: 90px;
  width: 100%;
  position: fixed;
  z-index: 5000;
}

.header-nav {
  background: white;
  height: 90px;
  width: 100%;
  display: flex;
  position: relative;
}

.header-logo {
  width: 160px;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0%;
}

.logo-link {
  height: 100%;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  left: 20%;
  top: 0;

  img {
    height: 30px;
    width: 160px;
  }
}
.nav-links {
  height: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
  white-space: nowrap;
  font-size: 0.9em;
  position: absolute;
  right: 2%;

  li {
    list-style-type: none;
    display: flex;
    min-width: 220px;
    align-items: center;
    justify-content: center;

    a {
      color: black;
      text-decoration: none;
      font-size: 1.5em;
      letter-spacing: 2px;
      /* &.router-link-active {
        border-bottom: 1px solid black;
        padding-bottom: 5px;
      } */
    }
  }
}

@media only screen and (max-width: 980px) {
  #lg-links {
    display: none;
  }
}
@media only screen and (max-width: 460px) {
  #lfw-logo {
  }
}
@media only screen and (min-width: 980px) {
  #dropdown-right {
    display: none;
  }
}
</style>