<template>
  <div class="oppskrifter-container">
    <h1>Prøv våre spennende oppskrifter</h1>
    <div class="filter">
      <span>Filtrer på oppskrifter</span>
      <select v-model="selected">
        Alle oppskrifter
        <option>Alle</option>
        <option>Varmretter</option>
        <option>Kaldretter</option>
        <option>Grill</option>
        <option>Sommer</option>
        <option>Vinter</option>
      </select>
    </div>
    <section class="oppskrifter-flexbox">
      <ul class="oppskrift">
        <li
          class="oppskrift-link"
          v-for="oppskrift in filteredOppskrifter"
          :key="oppskrift.name"
        >
          <router-link
            :to="{
              name: 'Oppskrift',
              params: { slug: oppskrift.slug },
            }"
          >
            <img
              class="lazyload"
              :data-src="require(`@/assets/${oppskrift.image}`)"
            />
            <!-- <span>{{ oppskrift.sesong }}</span> -->
            <span>{{ oppskrift.name }}</span>
          </router-link>
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
import storetwo from "../storetwo";
export default {
  data() {
    return {
      oppskrifter: storetwo.oppskrifter,
      selected: "Alle",
    };
  },

  computed: {
    filteredOppskrifter: function () {
      return this.oppskrifter.filter((oppskrift) => {
        return oppskrift.sesong.includes(this.selected);
      });
    },
  },
  mounted() {
    window.scrollTo(0, 0);
  },
};
</script>

<style lang="scss" scoped>
h1 {
  font-size: 2em;
  padding: 80px 0px;
}

.oppskrifter-container {
  position: relative;
  display: flex;
  align-items: center;
  height: 100%;
  width: 100%;
  justify-content: center;
  flex-direction: column;
  background: rgba(0, 0, 0, 0.945);

  color: white;

  h1 {
    text-align: center;
  }

  .filter {
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 50%;
    flex-wrap: wrap;
    span {
      font-size: 1.5em;
      text-align: center;
      flex: 0 1 25%;
      min-width: 200px;
    }
    select {
      flex: 0 1 25%;
      min-width: 200px;
      padding: 10px;
      position: relative;
      font-size: 1.2em;

      option {
      }

      select::after {
        content: "";
        position: absolute;
      }
    }
  }
}

.oppskrifter-flexbox {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  padding-bottom: 40px;

  .oppskrift {
    display: flex;
    align-items: center;
    justify-content: center;
    list-style-type: none;
    width: 80%;
    height: 100%;
    flex-wrap: wrap;

    .oppskrift-link {
      height: fit-content;
      width: 100%;
      display: flex;
      flex: 0 1 25%;
      min-width: 320px;
      margin: 10px;

      a {
        height: fit-content;
        width: 100%;
        color: white;
        text-decoration: none;
        display: flex;
        flex-direction: column;

        span {
          text-align: center;
          margin-top: 20px;
          font-size: 1.2em;
        }

        img {
          height: 100%;
          width: 100%;
        }
      }
    }
  }
}
</style>