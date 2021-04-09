<template>
  <div v-once>
    <section id="hero-section" class="hero-section">
      <div class="arktis-container">
        <div class="arktis-text">
          <h1>Barents</h1>
          <span>Vår nye hvalburger</span>
          <a href="#">Finn i butikk</a>
        </div>
      </div>
    </section>
    <section class="hero-section-2">
      <div class="above1760">
        <!--whitespace-->
      </div>
      <div class="svg-box">
        <!--samme løsningen som med img-box, wrapper-->
        <svg viewBox="0 0 auto 200">
          <!--this value has to be the same as svg-box height (the svg box is set to pixels)-->

          <defs>
            <mask id="mask" x="0" y="0" height="100%" width="100%">
              <rect x="0" y="0" height="100%" width="100vw" />
              <text
                x="50%"
                y="50%"
                fill="black"
                text-anchor="middle"
                fill-opacity="1"
              >
                Lofothval
              </text>
            </mask>
          </defs>
          <rect x="0" y="0" height="100%" width="100vw" />
        </svg>
      </div>
      <div class="belowlofothval">
        <div class="belowlofothvaltext">
          <h2>Ren tradisjon</h2>
        </div>
      </div>
      <div class="whitespacediv-three">
        <!--whitespace-->
      </div>

      <div class="below1760">
        <div class="below1760text">
          <h3>Våre produkter</h3>
        </div>
      </div>
      <div class="ourcreations">
        <div class="left-arrow" @click="moveLeft">
          <b-icon
            icon="arrow-left-circle-fill"
            aria-hidden="true"
            style="height: 50px; width: 50px; color: white"
          ></b-icon>
        </div>
        <div class="right-arrow" @click="moveRight">
          <b-icon
            icon="arrow-right-circle-fill"
            style="height: 50px; width: 50px; color: white"
            aria-hidden="true"
          ></b-icon>
        </div>
        <div class="creations-wrapper" ref="prod">
          <!--flex container-->
          <router-link
            :to="{ name: 'ProduktInfo', params: { slug: produkt.slug } }"
            v-for="produkt in produkter"
            :key="produkt.name"
          >
            <img
              :src="require(`@/assets/${produkt.image}`)"
              alt="lettrøkt hvalkjøtt"
            />
            <span>{{ produkt.name }}</span>
          </router-link>
        </div>
      </div>

      <div class="her-collection">
        <div class="collections-wrapper">
          <!--grid container-->
          <router-link
            v-for="spesialitet in spesial"
            :key="spesialitet.name"
            :to="{ name: 'Spesial', params: { slug: spesialitet.slug } }"
          >
            <img
              :src="require(`@/assets/${spesialitet.image}`)"
              alt="lettrøkt hvalkjøtt"
            />
          </router-link>
          <div class="collections-text-header">
            <h1>Superior hvalbiff</h1>
            <p>
              Utforsk det ypperste og mest ettertraktede produktet innen nordisk
              tradisjonsfiske
            </p>
          </div>
        </div>
      </div>

      <div class="oppskrifter">
        <div class="whitebox">
          <div class="oppskrifter-text">
            <h6>Ekstraordinær råvare</h6>
            <span>Oppskrifter & inspirasjon</span>
            <router-link to="/oppskrifter">Klikk her</router-link>
          </div>
        </div>
      </div>
      <div class="whitespacediv"></div>

      <div class="parallax">
        <!--this has pos relatve, background-img pos fixed etc...-->
        <div class="overlaydark">
          <div class="overlaytext">
            <!--this has pos absolute-->
            <span id="span1overlay">Mesterlig håndtverk</span>
            <span id="span2overlay">Se hvordan vi gjør det</span>
            <router-link :to="{ name: 'Handmade' }">Klikk her</router-link>
          </div>
        </div>
      </div>

      <div class="below-restaurant">
        <div class="below-restaurant-text">
          <p>Våre verdier</p>
        </div>
      </div>

      <div class="benefits-cards">
        <!--grid container-->
        <div class="benefits-cards-wrapper1">
          <!--flex container-->
          <a href="#">
            <img src="@/assets/640x427-minke-whale.png" alt="minke hval" />
          </a>
          <h1>Etisk ansvar</h1>
          <p>
            Forvaltningen av hvalfangst er basert på vitenskapelige råd, og
            underlagt strengt kontroll- og utøvelsesregelverk, både nasjonalt og
            internasjonalt. Les mer om våre etiske forpliktelser her.
          </p>
          <div class="les-mer1">
            <a href="#">Les mer</a>
          </div>
        </div>

        <div class="benefits-cards-wrapper1">
          <!--flex container-->
          <a href="#">
            <img src="@/assets/gun.png" alt="sirkulær økonomi" />
          </a>
          <h1>Bærekraft</h1>
          <p>
            Bærekraftig mat er mat som inngår i bærekraftige produksjoner og som
            fraktes via miljøvennlig transport. "Dette strekker vi oss langt
            etter." Les mer om våre bærekraftmål her.
          </p>
          <div class="les-mer1">
            <a href="#">Les mer</a>
          </div>
        </div>

        <div class="benefits-cards-wrapper1">
          <!--flex container-->
          <a href="#">
            <img
              src="@/assets/2c045c01-a714-41a0-939f-af81cbe8bc3b.jpg"
              alt="helsegevinst"
            />
          </a>
          <h1>Helsegevinst</h1>
          <p>
            Hvalkjøtt inneholder nemlig næringsstoffer som: Omega 3 med de
            helseriktige stoffene DPA og EPA. Jern, Vitamin A,Vitamin D.
            Vitaminer fra B-gruppen som B6 og B12.
          </p>
          <div class="les-mer1">
            <a href="#">Les mer</a>
          </div>
        </div>
      </div>

      <div class="whitespacediv-three"></div>
    </section>
  </div>
</template>

<script>
import store from "../store";
export default {
  name: "Home",

  data() {
    return {
      produkter: store.produkter,
      spesial: store.spesial,
    };
  },
  methods: {
    moveLeft() {
      this.$refs.prod.scrollLeft += -300;
    },
    moveRight() {
      this.$refs.prod.scrollLeft += 300;
    },
  },
};
</script>

<style lang="scss" scoped>
.hero-section {
  height: 100vh;
  width: 100%;
  position: fixed;
  top: 0;
  z-index: 1002;
  opacity: 1;
  background-image: url("~@/assets/pexels-valeria-boltneva-1639562.jpg");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;

  .arktis-container {
    height: 100%;
    width: 280px;
    display: flex;
    position: absolute;
    top: 100px;
    left: 9.58333333333333%;
    background: transparent;
    flex-direction: column;

    .arktis-text {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      height: 500px;
      width: 100%;

      h1 {
        font-size: 4em;
        color: white;
        font-weight: 200;
      }

      span {
        font-size: 1.5em;
        color: white;
      }
      a {
        text-decoration: none;
        font-size: 1.5em;
        color: white;
        border: 3px solid rgb(255, 255, 255);
        padding: 10px;
        margin-top: 30px;
      }
      a:hover {
        background: black;
        color: white;
        transition: all 0.5s;
      }
    }
  }
}

//SECTION 2
//SECTION 2
//SECTION 2
//SECTION 2

@import url("https://fonts.googleapis.com/css2?family=Dancing+Script&display=swap");
.belowlofothval {
  height: 50px;
  width: 100%;
  color: black;
  margin-top: -4px;

  .belowlofothvaltext {
    //margin-top: 50px;
    max-height: 150px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    font-family: montserrat;
    white-space: nowrap;
    line-height: 50px;
    background: white;

    h2 {
      font-size: 1.7em;
      font-weight: 200;
      letter-spacing: 3px;
    }

    h3 {
      font-size: 1.5em;
      font-weight: 200;
      letter-spacing: 3px;
    }
  }
}

.above1760 {
  height: 75px;
  background: white;
  margin-bottom: -1.5px; // det her fjerner streker som kommer av at to elementer ligger helt, men ikke 100% inntil hverandre
  width: 100%;
}

.below1760 {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 200px;
  //position: relative;
  background: white;
  margin-top: -4px; //fjerner streken av to elementer som ikke ligger helt inntil hverandre
}

svg {
  font-size: 8em;
  letter-spacing: 5px;
  font-family: montserrat;
  font-weight: 900;
  justify-self: center;
  align-self: center;
  height: 100%;
  width: 100%;
}

svg rect {
  fill: white;
  mask: url(#mask);
}

.svg-box {
  height: 100%;
  width: 100%;
  overflow-x: hidden;
  overflow-y: hidden;
  position: relative;

  bottom: 0;
  right: 0;
}

.hero-section-2 {
  height: fit-content;
  width: 100%;
  margin-top: 0;
  z-index: 1003;
  cursor: initial;
  position: absolute;
  top: 100%;
  left: 0;
  //background: transparent;
  overflow-x: hidden;
  overflow-y: hidden;
}

.below1760text {
  width: fit-content; //eller fit content
  max-height: 150px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: montserrat;
  white-space: nowrap;
  border-bottom: 1px solid black;
  margin-bottom: 20px;
  line-height: 100px;

  h3 {
    text-align: center;
    font-size: 1.5em;
    font-weight: 200;
    letter-spacing: 3px;
  }
}

.ourcreations {
  width: 100%;
  //height: fit-content;
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;

  .left-arrow {
    height: 100%;
    width: 50px;
    background: transparent;
    position: absolute;
    left: 2%;
    top: 0;
    z-index: 500;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .right-arrow {
    height: 100%;
    width: 50px;
    background: transparent;
    position: absolute;
    right: 2%;
    top: 0;
    z-index: 500;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

.ourcreations div a img:hover,
.ourcreations div a img:focus {
  transition: 1s ease;
  transform: translateY(-10px);
}

.creations-wrapper {
  width: 100%;
  //height: fit-content;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  overflow-x: scroll;
  scrollbar-width: none;
  white-space: nowrap;
  scroll-behavior: smooth;
  scroll-snap-type: x mandatory;
  gap: 10px;
  margin: 0px 20px;

  a {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: montserrat;
    font-weight: 700;
    text-decoration: none;
    text-transform: uppercase;
    color: black;

    min-width: 220px;
    flex: 0 1 25%;
  }

  a img {
    width: 100%;
    height: 100%;
    cursor: pointer;
  }

  span {
    font-size: 1em;
    letter-spacing: 1px;
    text-align: center;
    font-weight: 200;
    margin-top: 20px;
    max-height: 20px;
  }
}

.her-collection {
  width: 100%;
  background: white;
}

.collections-wrapper {
  height: 100%;
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  column-gap: 40px;
  row-gap: 40px;
  padding: 50px 20px;
  margin-top: -4px;

  a {
    min-width: 320px;
    flex: 1 1 10%;
    max-width: 500px;
  }

  a img {
    height: 100%;
    width: 100%;
  }
  a:hover {
    transform: translateY(-10px);
    transition: all 1s;
  }
}

.collections-text-header {
  //height: 250px;

  display: flex;
  flex: 1 1 10%;
  flex-direction: column;
  font-family: montserrat;
  justify-content: center;
  //align-items: center;
  letter-spacing: 1px;
  min-width: 320px;

  h1 {
    font-size: 1.6em;
    font-weight: 200;
    margin-bottom: 30px;
  }
  p {
    font-size: 1em;
    line-height: 50px;
  }
}

.whitespacediv {
  width: 100%;
  background: white;
  height: 50px;
}
.whitespacediv-three {
  width: 100%;
  background: white;
  height: 100px;
  margin-top: -24px;
}

.oppskrifter {
  background: white;
  height: 600px;
  width: 100%;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  background-image: url("~@/assets/pexels-valeria-boltneva-1639557.jpg");
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  font-family: montserrat;

  .whitebox {
    background: rgba(255, 255, 255, 0.726);
    display: flex;
    min-width: 220px;
    height: 300px;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    .oppskrifter-text {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-evenly;
      height: 200px;
      padding: 60px;

      min-width: 220px;
    }

    h6 {
      color: black;
      letter-spacing: 0.8px;
      text-align: center;
      font-size: 4em;
      font-family: "Dancing Script", cursive;
    }

    span {
      color: black;
      letter-spacing: 0.9px;
      font-size: 2em;
      text-align: center;
    }
    a {
      color: black;
      padding: 10px;
      border: 2px solid black;
      width: 150px;
      font-size: 1.5em;
      letter-spacing: 0.9px;
      text-align: center;
      text-decoration: none;
      margin-top: 20px;
    }

    a:hover {
      transition: all 0.5s;
      background: black;
      color: white;
    }
  }
}

.parallax {
  height: 600px;
  background-image: url("~@/assets/a57fb2b9ec24a9f074035c5290585c1e.jpg");
  position: relative;
  opacity: 1;
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;

  .overlaydark {
    height: 100%;
    width: 100%;
    background: rgba(0, 0, 0, 0.699);
    z-index: 2000;
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;

    .overlaytext {
      height: 100%;
      min-width: 220px;
      text-align: center;
      padding: 60px;
      font-family: montserrat;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      background: rgba(0, 0, 0, 0.6);

      #span1overlay {
        font-size: 2.5em;
        letter-spacing: 3px;
        color: rgb(255, 255, 255);
        font-weight: 900;
        padding: 20px 0;
      }

      #span2overlay {
        font-size: 1.5em;
        letter-spacing: 0.9px;
        color: white;
        padding-bottom: 50px;
      }

      a {
        text-decoration: none;
        font-size: 1.5em;
        letter-spacing: 0.9px;
        border: 1px solid white;
        color: white;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 150px;
        height: 50px;
        font-weight: 900;
      }

      a:hover {
        background: white;
        color: black;
        transition: all 0.5s;
      }
    }
  }
}

.below-parallax {
  width: 100%;
  height: 300px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: white;

  .below-parallax-text {
    //margin-top: 50px;
    max-height: 150px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    font-family: montserrat;
    white-space: nowrap;
    border-bottom: 1px solid black;
    line-height: 50px;
    width: 300px; //justerer understreken

    margin-bottom: 20px;

    p {
      font-size: 1.5em;
      font-weight: 200;
      letter-spacing: 3px;
    }
  }
}

.below-restaurant {
  width: 100%;
  height: 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: white;

  .below-restaurant-text {
    //margin-top: 50px;
    max-height: 150px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    font-family: montserrat;
    white-space: nowrap;
    border-bottom: 1px solid black;
    line-height: 50px;
    width: 300px; //justerer understreken

    margin-bottom: 20px;

    p {
      font-size: 1.5em;
      font-weight: 200;
      letter-spacing: 3px;
    }
  }
}

.benefits-cards {
  background: white;
  width: 100%;
  height: 100%;
  display: flex;
  flex-wrap: wrap;
  //grid-auto-rows: 500px;
  column-gap: 20px;
  row-gap: 50px;
  align-items: center;
  justify-content: center;
  font-family: montserrat;
  color: black;
  //padding-top: 50px;
  padding-left: 50px;
  padding-right: 50px;
  padding-bottom: 50px;
}

.benefits-cards-wrapper1 {
  height: fit-content;
  min-width: 220px;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex: 0 1 320px;
  a {
    text-decoration: none;
  }
  h1 {
    margin-top: 20px;
    font-size: 1.5em;
    font-weight: 200;
    letter-spacing: 1px;
  }
  p {
    font-size: 1em;
    letter-spacing: 0.8px;
    margin-top: 22px;
    padding: 10px;
  }

  a img {
    width: 100%;
    height: 100%;
  }
}

.les-mer1 {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
  margin-top: 50px;

  a {
    text-decoration: none;
    color: black;
    border: 1px solid rgb(0, 0, 0);

    padding: 10px;
    font-weight: 900;
  }
}

.whitespacediv-two {
  height: 200px;
  background: white;
  width: 100%;
}

.les-mer1 a:hover,
.les-mer1 a:focus-within {
  background: rgb(0, 0, 0);
  color: white;
  transition: all 0.5s;
}

@media only screen and (max-width: 520px) {
  svg {
    font-size: 6em;
  }
}
@media only screen and (max-width: 420px) {
  svg {
    font-size: 5em;
  }
}
</style>
