<template>
  <div id="landing-page" v-once>
    <div id="carousel-container">
      <b-carousel
        id="carousel-1"
        v-model="slide"
        :interval="4000"
        controls
        indicators
        background="#ababab"
        img-width="1024"
        img-height="480"
        style="text-shadow: 1px 1px 2px #333"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
      >
        <b-carousel-slide v-for="campaign in campaigns" :key="campaign.name">
          <template #img>
            <img
              id="carousel-img"
              class="d-block img-fluid w-100"
              width="1024"
              height="480"
              :src="require(`@/assets/jpg/${campaign.image}`)"
              alt="image slot"
            />
          </template>
        </b-carousel-slide>
      </b-carousel>
    </div>

    <section class="hero-section-overlap">
      <!-- <div class="above1760">
      </div> -->

      <div class="below1760">
        <div class="below1760text">
          <h3>Våre produkter</h3>
        </div>
      </div>
      <div class="ourcreations">
        <div class="left-arrow" @click="moveLeft">
          <b-icon
            icon="chevron-left"
            aria-hidden="true"
            style="height: 50px; width: 50px; color: white"
          ></b-icon>
        </div>
        <div class="right-arrow" @click="moveRight">
          <b-icon
            icon="chevron-right"
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
              class="lazyload"
              :data-src="require(`@/assets/jpg/${produkt.image}`)"
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
              :src="require(`@/assets/jpg/${spesialitet.image}`)"
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
        <picture>
          <source
            srcset="
              @/assets/webP/pexels-valeria-boltneva-1639557-min-25.webp 1627w,
              @/assets/webP/pexels-valeria-boltneva-1639557-min-33.webp 2169w
            "
          />
          <source
            srcset="
              @/assets/jpg/pexels-valeria-boltneva-1639557-min-25.jpg 1627w,
              @/assets/jpg/pexels-valeria-boltneva-1639557-min-33.jpg 2169w
            "
          />
          <img
            data-src="@/assets/jpg/pexels-valeria-boltneva-1639557-min-25.jpg"
            alt="delicious recipe"
            class="recipe-img lazyload"
          />
        </picture>
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

      <div class="whitespacediv-three"></div>
      <footer class="kontakt-info-felt">
        <!--grid container-->

        <div class="footer-logo-container">
          <div class="footer-logo-flexbox">
            <div class="logobox"></div>
            <span>Hvalprodukter</span>
          </div>
        </div>

        <div class="kontakt-info-container">
          <div class="kontakt-info-flexbox">
            <span>Lofothval AS</span>
            <span>8390 Reine</span>
            <span>Norway</span>
            <span>Email:</span>
            <span>tel:</span>
          </div>
        </div>

        <div class="follow-us-container">
          <div class="follow-us-flexbox">
            <span>Følg oss på:</span>
            <div class="sns-flexbox">
              <a href="#">
                <img src="@/assets/png/sns1_1-min.png" alt="instagram icon" />
              </a>
              <a href="#">
                <img src="@/assets/png/sns1_2-min.png" alt="twitter icon" />
              </a>
              <a href="#">
                <img src="@/assets/png/sns1_3-min.png" alt="vimeo icon" />
              </a>
            </div>
          </div>
        </div>
      </footer>
    </section>
  </div>
</template>

<script>
import store from "../store";
import campaignstore from "../campaignstore";
export default {
  name: "Home",

  data() {
    return {
      produkter: store.produkter,
      spesial: store.spesial,
      campaigns: campaignstore.campaigns,
      slide: 0,
      sliding: null,
    };
  },
  methods: {
    moveLeft() {
      this.$refs.prod.scrollLeft += -300;
    },
    moveRight() {
      this.$refs.prod.scrollLeft += 300;
    },

    onSlideStart(slide) {
      this.sliding = true;
    },
    onSlideEnd(slide) {
      this.sliding = false;
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Dancing+Script&display=block");
#landing-page {
  height: 100%;
  position: relative;
  width: 100%;
  background: white;
}

#carousel-1 {
  height: fit-content;
  width: 100%;
  background-color: black;
}

.carousel-item {
  width: 100%;
  height: 70vh;
}

#carousel-img {
  height: 100%;
  width: 100%;
  object-fit: contain;
}
//SECTION 2
//SECTION 2
//SECTION 2
//SECTION 2

.belowlofothval {
  width: 100%;

  .belowlofothvaltext {
    height: 50px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: montserrat;
    white-space: nowrap;
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

.below1760 {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 160px;
  min-width: 100%;
  background: white;
}

.hero-section-overlap {
  height: fit-content;
  width: 100%;
  margin-top: 0;
  z-index: 1003;
  cursor: initial;
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
    left: 7%;
    top: 0%;
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
    right: 7%;
    top: 0%;
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

    min-width: 320px;
    flex: 0 1 25%;

    margin: 0px 10px;
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
  height: fit-content;
  width: 100%;
  /* background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  background-image: url("~@/assets/pexels-valeria-boltneva-1639557.jpg"); */
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  font-family: montserrat;
  position: relative;

  .whitebox {
    background: rgba(255, 255, 255, 0.726);
    display: flex;
    min-width: 220px;
    height: 300px;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    position: absolute;

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
      white-space: nowrap;
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

.recipe-img {
  height: 600px;
  width: 100%;
  object-fit: cover;
}

.parallax {
  height: 600px;
  background-image: url("~@/assets/jpg/a57fb2b9ec24a9f074035c5290585c1e-min.jpg");
  position: relative;
  opacity: 1;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;

  .overlaydark {
    height: 100%;
    width: 100%;
    background: rgba(0, 0, 0, 0.5);
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
      background: rgba(0, 0, 0, 0.95);

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

.kontakt-info-felt {
  height: 100%;
  width: 100%;
  background: rgb(199, 199, 199);
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  padding: 0 50px;
  align-items: center;
  justify-content: center;
  position: relative;
  bottom: 0;
}

.footer-logo-container {
  font-family: montserrat;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;

  .footer-logo-flexbox {
    display: flex;
    width: 150px;
    height: 100px;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    span {
      font-size: 1.3em;
      width: 100%;
      text-align: center;
    }

    .logobox {
      background-image: url("~@/assets/png/Lofothval_sort-min.png");
      height: 100px;
      width: 150px;
      background-repeat: no-repeat;
      background-size: contain;
      background-position: center;
    }
  }
}

.kontakt-info-container {
  width: 100%;
  height: 150px;
  font-family: montserrat;
  display: flex;
  align-items: center;
  justify-content: center;

  .kontakt-info-flexbox {
    width: 150px;
    height: fit-content;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;

    span {
      font-size: 1.2em;
      width: 100px;
    }
  }
}

.follow-us-container {
  font-family: montserrat;
  height: 100%;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;

  .follow-us-flexbox {
    display: flex;
    flex-direction: row;
    height: 200px;
    width: 300px;
    align-items: center;

    span {
      width: 100%;
      text-align: center;
    }

    .sns-flexbox {
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: space-evenly;
      height: 200px;

      a {
        img {
          height: 30px;
          width: 30px;
        }
      }
    }
  }
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
