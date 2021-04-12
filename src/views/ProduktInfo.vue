<template>
  <div class="produkt-info-container">
    <div
      class="produkt-info-flexbox"
      v-for="info in produkt.produktinfo"
      :key="info.title"
    >
      <div class="produkt-info-header">
        <span id="info">{{ info.title }}</span>
        <img :src="require(`@/assets/${info.image}`)" :alt="info.title" />
      </div>
      <div class="produkt-beskrivelse" id="produkt-intro">
        <p>{{ slug }}</p>
        <p>{{ slug }}</p>
      </div>

      <div class="produkt-spesifikasjoner">
        <span>Spesifikasjoner</span>
      </div>

      <div class="produkt-beskrivelse">
        <h6>Ingredienser</h6>
        <p>{{ info.ingredienser }}</p>
      </div>

      <div class="produkt-beskrivelse">
        <h6>Vekt</h6>
        <p id="vekt">{{ info.vekt }}</p>
      </div>

      <div class="produkt-beskrivelse">
        <h6>Oppbevaring</h6>
        <p>{{ info.oppbevaring }}</p>
      </div>
      <div class="produkt-beskrivelse">
        <h6 id="ninnhold">Næringsinnhold per 100g</h6>
        <table id="tabell">
          <tbody>
            <tr>
              <td>Energi (kJ)</td>
              <td class="right-text">100 kJ</td>
            </tr>
            <tr>
              <td>Energi (kcal)</td>
              <td class="right-text">200 kcal</td>
            </tr>
            <tr>
              <td>Fett</td>
              <td class="right-text">10 g</td>
            </tr>
            <tr>
              <td>-Mettet fett</td>
              <td class="right-text">5 g</td>
            </tr>
            <tr>
              <td>-Enumettet fett</td>
              <td class="right-text">50 g</td>
            </tr>
            <tr>
              <td>-Flerumettet fett</td>
              <td class="right-text">15 g</td>
            </tr>
            <tr>
              <td>Karbohydrater</td>
              <td class="right-text">0 g</td>
            </tr>
            <tr>
              <td>Sukker</td>
              <td class="right-text">0 g</td>
            </tr>
            <tr>
              <td>Protein</td>
              <td class="right-text">20 g</td>
            </tr>
            <tr>
              <td>Salt</td>
              <td class="right-text">0.05 g</td>
            </tr>
          </tbody>
        </table>
      </div>

      <div class="produkt-beskrivelse">
        <h6>Forpakning</h6>
        <p>
          Lorem ipsum dolor sit amet consectetur, adipisicing elit. Fuga
          provident distinctio perspiciatis tempore sequi ad commodi doloremque
          cumque nesciunt, magni maxime voluptate, facilis error sint ratione
          sit eveniet similique. Ex.
        </p>
      </div>
      <div class="produkt-beskrivelse">
        <h6>Allergener</h6>
        <p>Melk</p>
      </div>
    </div>
  </div>
</template>

<script>
import store from "../store";
export default {
  data() {
    return {};
  },

  props: {
    slug: {
      type: String,
      required: true,
    },
  },

  computed: {
    produkt() {
      return store.produkter.find((produkt) => produkt.slug === this.slug);
    },

    info() {
      return this.produkt.produktinfo.find(
        (info) => info.slug === this.infoSlug
      );
    },
  },

  mounted() {
    window.scrollTo(0, 0);
  },
};
</script>

<style lang="scss" scoped>
.produkt-info-container {
  background: rgba(0, 0, 0, 0.945);
  display: flex;
  color: white;
  justify-content: center;
}
.produkt-info-header {
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  height: fit-content;
  flex-direction: column;
  img {
    height: 250px;
    margin: 40px 0px;
  }

  span {
    font-size: 3em;
    font-weight: 300;
  }
}

#produkt-intro {
  border: 3px solid black;
}
.produkt-spesifikasjoner {
  height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  span {
    font-size: 1.5em;
    border-bottom: 1px solid black;
    padding-bottom: 10px;
  }
}
.produkt-beskrivelse {
  align-items: center;
  justify-content: center;
  display: flex;
  flex-wrap: wrap;
  min-height: 100px;
  min-width: 300px;
  padding: 20px;
}
.produkt-info-flexbox {
  padding: 50px 50px;
  width: calc(1440px / 2);
}
.produkt-beskrivelse:nth-child(even) {
  background: rgba(230, 230, 230, 0.5);
}

.produkt-beskrivelse > *:nth-child(1) {
  flex: 1 1 35%;
  font-size: 1.5em;
  font-weight: 200;
}
.produkt-beskrivelse > *:nth-child(2) {
  flex: 1 1 65%;
  min-width: 300px;
  font-size: 1.2em;
}
table {
  height: 100%;
  width: 100%;
  display: flex;
  flex: 1 0 280px;
  tbody {
    tr {
    }
    td {
    }
    .right-text {
      text-align: right;
    }
  }

  tr:nth-child(odd) {
    background: rgb(230, 230, 230);
    color: black;
  }
}

#produkt-intro {
  text-align: center;
}

#tabell {
  flex: 1 1 10%;

  justify-content: center;
}

#ninnhold {
  text-align: center;
  white-space: nowrap;
}
</style>