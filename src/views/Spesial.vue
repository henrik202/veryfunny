<template>
  <div class="spesial-container">
    <div class="spesial-header">
      <h2>Superior hvalbiff</h2>
    </div>

    <section class="spesial-banner">
      <div class="banner-overlay"></div>
    </section>
    <div class="banner-below">
      <div class="spesial-description">
        <h3>Superior Hvalbiff</h3>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum
          perferendis nesciunt placeat amet natus, aspernatur cum fugiat non
          repudiandae dolorum ex ullam optio qui quod ut quaerat vero eos ab.
        </p>

        <div class="produkt-beskrivelse">
          <h6>Næringsinnhold per 100g</h6>
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
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    window.scrollTo(0, 0);
  },
};
</script>

<style lang="scss" scoped>
.spesial-container {
  width: 100%;
  height: 100%;
  background: black;

  .spesial-header {
    height: 200px;
    width: 100%;
    padding: 0px 40px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    background: rgb(0, 0, 0);

    h2 {
      font-size: 2.5em;
      font-weight: 300;
      letter-spacing: 2px;
      color: white;
    }
  }

  .spesial-banner {
    width: 100%;
    background: rgba(0, 0, 0, 0.95);
    background-image: url("~@/assets/pexels-valeria-boltneva-1639562.jpg");
    height: 500px;
    background-position: center;
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
    position: relative;

    .banner-overlay {
      position: absolute;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.295);

      display: flex;

      .banner-text {
        color: white;
        height: 100%;
      }
    }
  }

  .banner-below {
    width: 100%;
    height: fit-content;
    background: rgb(0, 0, 0);
    display: flex;
    padding: 20px 50px;

    .spesial-description {
      width: 80%;
      height: 100%;
      color: white;

      h3 {
        font-size: 2em;
      }

      p {
        font-size: 1.2em;
        margin-top: 20px;
      }

      .produkt-beskrivelse {
        align-items: center;
        justify-content: center;
        display: flex;
        flex-wrap: wrap;
        flex-direction: column;
        height: fit-content;
        min-width: 300px;
        padding: 20px;

        h6 {
          width: 100%;
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
      }
    }
  }
}

@media only screen and (max-width: 960px) {
}
</style>