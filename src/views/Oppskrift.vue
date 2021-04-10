<template>
  <div class="oppskrifter-info-container">
    <div class="info-title">
      <h1>{{ info.name }}</h1>
    </div>
    <div
      class="oppskrift-header"
      v-for="info in oppskrift.oppskriftinfo"
      :key="info.name"
    >
      <div class="opps-img">
        <div class="oppskrift-img">
          <img :src="require(`@/assets/${info.image}`)" />
        </div>
        <div class="ingredienser">
          <div>
            <h6>Ingredienser</h6>
            <span>Vann</span>
            <span>Smør</span>
            <span>Melk</span>
            <span>Hvetemel</span>
            <span>4 stk {{ info.ingrediens }}</span>
            <span>Tomater</span>
            <span>Paprika</span>
          </div>
        </div>
      </div>
      <div class="phrases">
        <p>{{ info.phrase }}</p>
        <p>{{ info.anbefaling }}</p>
        <p>Velbekomme,</p>
      </div>

      <div class="porsjoner">
        <div>
          <b-icon icon="receipt" shift-h="-10" scale="1.5"></b-icon>
          <span>3-4 porsjoner </span>
          <b-icon icon="alarm" shift-h="-10" scale="1.5"></b-icon>
          <span>25 min </span>
        </div>
      </div>
      <ol class="fremgang">
        <li>
          <p>
            1. Start med å sylte rødløk slik at den er klar til servering. Rens
            løken og legg over i ett glass. Kok opp vann, sukker og eddik til
            sukkeret er oppløst og hell laken over rødløken. La det stå frem til
            servering.
          </p>
        </li>
        <li>
          <p>
            2. Tilbered burgeren etter anvisning på pakken og varm brødene i en
            tørr stekepanne.
          </p>
        </li>
        <li>
          <p>
            3. Anrett bruger med remulade, ruccola, lofotburger og syltet
            rødløk.
          </p>
        </li>
        <li><p>Velbekomme!</p></li>
      </ol>
    </div>
    <div class="produkter-below">Våre produkter</div>
    <div class="produkt-container">
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
      <div class="produkt-flexbox" ref="prod">
        <router-link
          v-for="produkt in produkter"
          :key="produkt.name"
          :to="{
            name: 'ProduktInfo',
            params: { slug: produkt.slug },
            hash: '#info',
          }"
        >
          <img
            :src="require(`@/assets/${produkt.image}`)"
            alt="lettrøkt hvalkjøtt"
          />
          <span>{{ produkt.name }}</span>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import storetwo from "../storetwo";
import store from "../store";
export default {
  data() {
    return {
      produkter: store.produkter,
    };
  },

  props: {
    slug: {
      type: String,
      required: true,
    },
  },

  methods: {
    moveLeft() {
      this.$refs.prod.scrollLeft += -300;
    },
    moveRight() {
      this.$refs.prod.scrollLeft += 300;
    },
  },

  computed: {
    oppskrift() {
      return storetwo.oppskrifter.find(
        (oppskrift) => oppskrift.slug === this.slug
      );
    },

    info() {
      return this.oppskrift.oppskriftinfo.find(
        (info) => info.slug === this.infoSlug
      );
    },
  },
};
</script>

<style lang="scss" scoped>
.oppskrifter-info-container {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
  background: rgba(0, 0, 0, 0.945);

  .info-title {
    width: 80%;
    height: 200px;
    display: flex;
    align-items: center;
    color: white;
  }

  .oppskrift-header {
    width: 80%;
    height: 100%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: flex-start;
  }
}

.opps-img {
  width: 100%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;

  .ingredienser {
    display: flex;
    flex-direction: column;
    justify-content: center;
    min-width: 320px;
    flex: 0 1 25%;
    align-items: flex-start;

    div {
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      color: white;

      h6 {
        font-size: 1.5em;
        margin-bottom: 20px;
      }
      span {
        font-size: 1.2em;
        padding: 5px 0px;
      }
    }
  }
  .oppskrift-img {
    height: fit-content;
    min-width: 280px;
    max-width: 320px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex: 0 1 25%;
    margin-bottom: 40px;
    margin-right: 150px;

    img {
      height: 100%;
      width: 100%;
    }
  }
}

.phrases {
  color: white;
  width: 100%;
  height: fit-content;
  display: flex;
  justify-content: space-around;
  flex-direction: column;
  margin-top: 40px;

  p {
    font-size: 1.5em;
    flex: 0 1 25%;
    height: fit-content;
    margin-bottom: 20px;
  }
}

.porsjoner {
  height: 100px;
  min-width: 320px;
  color: white;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;

  div {
    width: 100%;
    height: fit-content;
    display: flex;
    justify-content: center;
    align-items: center;

    span {
      flex: 0 1 50%;
      font-size: 1em;
      height: fit-content;
      position: relative;
    }
  }
}

.fremgang {
  height: fit-content;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  margin-bottom: 40px;

  li {
    height: fit-content;
    display: flex;
    color: white;

    p {
      font-size: 1.5em;
    }
  }
}

.produkt-container {
  position: relative;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.9);

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

.produkt-flexbox {
  display: flex;
  position: relative;
  align-items: flex-start;
  justify-content: flex-start;
  background: transparent;
  margin-bottom: 40px;
  width: 80%;
  gap: 2em;
  overflow-x: scroll;
  scrollbar-width: none;
  white-space: nowrap;
  scroll-behavior: smooth;
  scroll-snap-type: x mandatory;

  a {
    height: fit-content;
    min-width: 320px;
    flex: 0 1 25%;
    display: flex;
    flex-direction: column;
    position: relative;
    align-items: flex-start;
    justify-content: flex-start;
    scrollbar-width: none;

    text-decoration: none;

    /* img:hover {
      transform: scale(0.9);
      transition: all 1s ease;
    } */

    span {
      text-align: center;
      background: rgba(0, 0, 0, 0.589);
      width: 100%;
      color: white;
      position: absolute;
      bottom: 0;
      height: 50px;
      font-size: 1em;
      line-height: 50px;
    }

    img {
      height: 100%;
      width: 100%;
    }
  }
}

.produkter-below {
  height: 200px;
  width: 100%;
  background: black;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 2em;
}
</style>