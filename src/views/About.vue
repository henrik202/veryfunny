<template>
  <div class="about">
    <div class="about-header">
      <h1>En tradisjonsrik</h1>
      <h2><span>Sjømat</span><span>produsent</span></h2>
    </div>

    <section>
      <div class="section-header">
        <h2>En historie fra 20 år tilbake</h2>
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolore
          commodi nobis libero tempore. Eligendi, nesciunt! Assumenda nobis iste
          eligendi, impedit perspiciatis explicabo quo earum officia ab nisi
          quasi, repellendus corrupti.
        </p>
      </div>
      <ul class="history-timeline">
        <div class="watermark-box">
          <p>2006</p>
          <p>2010</p>
          <p>2016</p>
        </div>
        <li class="row-1">
          <div class="content-left">
            <div class="img-content">
              <img
                src="@/assets/jpg/2_000000000041-min.jpg"
                alt="Selskapslogo"
              />
            </div>
          </div>
          <div class="content-right">
            <div>
              <h2>2006</h2>
              <h3>Lofothval blir etablert</h3>
              <p>
                Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                Doloribus perferendis provident dolore consectetur quidem
                laudantium iusto repellendus, quod, natus adipisci distinctio!
                Eos facilis asperiores, quae neque unde sed fugit consequatur.
              </p>
            </div>
          </div>
        </li>
        <li class="row-2">
          <div class="content-left-row-2">
            <div>
              <h2>2006</h2>
              <h3>Lofothval blir etablert</h3>
              <p>
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
                Voluptas velit dolorum architecto impedit facilis illo expedita
                reprehenderit excepturi veritatis sint nostrum, laudantium,
                cupiditate libero? Incidunt fuga asperiores beatae deserunt
                atque.
              </p>
            </div>
          </div>
          <div class="content-right-row-2">
            <div class="img-content-row-2">
              <img
                src="@/assets/jpg/2_000000000041-min.jpg"
                alt="Selskapslogo"
              />
            </div>
          </div>
        </li>
        <li class="row-1">
          <div class="content-left">
            <div class="img-content">
              <img
                src="@/assets/jpg/2_000000000041-min.jpg"
                alt="Selskapslogo"
              />
            </div>
          </div>
          <div class="content-right">
            <div>
              <h2>2006</h2>
              <h3>Lofothval blir etablert</h3>
              <p>
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ex,
                molestias ad fuga eveniet quod voluptates nam aut hic sint
                voluptatem eligendi! Nostrum consequatur harum dolorem maxime.
                Cum facere saepe veniam.
              </p>
            </div>
          </div>
        </li>
        <li class="row-2">
          <div class="content-left-row-2">
            <div>
              <h2>2006</h2>
              <h3>Lofothval blir etablert</h3>
              <p>
                Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                Suscipit ipsa, aut odit, dignissimos vero possimus laboriosam
                exercitationem commodi consequuntur iste ea assumenda inventore
                nostrum impedit, veniam consectetur voluptate reprehenderit ut?
              </p>
            </div>
          </div>
          <div class="content-right-row-2">
            <div class="img-content-row-2">
              <img
                src="@/assets/jpg/2_000000000041-min.jpg"
                alt="Selskapslogo"
              />
            </div>
          </div>
        </li>
      </ul>
    </section>
    <div class="since"><p>Ren tradisjon</p></div>
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
  </div>
</template>

<script>
export default {
  setup() {},

  mounted() {
    window.scrollTo(0, 0);
  },
};
</script>

<style lang="scss" scoped>
.about {
  height: 100%;
  width: 100%;
}
.about-header {
  height: 250px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  flex-wrap: wrap;
  flex-direction: column;
  text-align: center;
  background: rgba(66, 66, 66, 0.3);

  h1 {
    font-size: 3em;
    letter-spacing: 1px;
    font-weight: 300;
    color: rgb(255, 255, 255);
  }

  h2 {
    margin-top: 20px;
    font-weight: 300;

    font-size: 2em;
    color: white;
  }
}

section {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.section-header {
  margin-top: 40px;
  display: flex;
  flex-direction: column;
  height: fit-content;
  width: 80%;
  align-items: center;
  justify-content: space-around;

  h2 {
    font-size: 2em;
    color: white;
  }
  p {
    font-size: 1.5em;
    margin-top: 40px;
    text-align: center;
    color: #6c757d;
  }
}

.history-timeline {
  height: fit-content;
  min-width: 220px;
  position: relative;
  list-style-type: none;
  margin-top: 80px;
  margin-left: 100px;
  margin-right: 100px;

  .watermark-box {
    z-index: 0;
    position: absolute;
    /* top: 5%; */
    right: 0%;
    height: 100%;
    min-width: 100%;
    background: transparent;
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: space-evenly;
    font-family: "Times New Roman", Times, serif;

    p {
      font-size: 12em;
      color: rgba(41, 30, 30, 0.4);
    }
  }
}
.history-timeline::before {
  content: "";
  position: absolute;
  width: 3px;
  background: rgba(41, 30, 30, 0.4);
  top: 0;
  bottom: 0;
  left: 50%;
  z-index: 0;
}

.content-right {
  z-index: 1;
  min-width: 120px;
  float: right;
  padding-left: 40px;
  height: fit-content;
  div {
    height: 100%;
    min-width: 120px;
    flex-wrap: wrap;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;

    h2 {
      font-size: 4em;
      font-weight: 900;
      color: white;
    }
    h3 {
      font-size: 3em;
      font-weight: 300;
      padding-top: 20px;
      color: white;
    }
    p {
      font-size: 1.5em;
      padding-top: 20px;
      color: #6c757d;
    }
  }
}
.content-left {
  z-index: 1;

  min-width: 120px;
  height: fit-content;
  padding-top: 50px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;

  .img-content {
    min-width: 120px;
    height: fit-content;
    border-radius: 50%;
    position: relative;

    img {
      width: 100%;
      height: 100%;
      border-radius: 50%;
    }
  }

  .arrow {
    height: 3px;
    width: 100%;
    background: rgba(0, 0, 0, 0.13);

    position: relative;
  }
}

.arrow::after {
  content: "";
  position: absolute;
  width: 25px;
  height: 25px;
  right: -14px;
  background-color: #d8cb9d;
  border: 3px solid #000;
  top: -12px;
  bottom: 0;
  border-radius: 50%;
}

.content-right-row-2 {
  z-index: 1;

  min-width: 120px;

  float: right;
  height: fit-content;

  padding-top: 50px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;

  .img-content-row-2 {
    min-width: 120px;
    height: fit-content;
    border-radius: 50%;
    position: relative;

    img {
      width: 100%;
      height: 100%;
      border-radius: 50%;
    }
  }

  .arrow-row-2 {
    height: 3px;
    width: 100%;
    background: rgba(0, 0, 0, 0.13);

    position: relative;
  }
}

.arrow-row-2::after {
  content: "";
  position: absolute;
  width: 25px;
  height: 25px;
  left: -10px;
  background-color: #d8cb9d;
  border: 3px solid #000;
  top: -12px;
  bottom: 0;
  border-radius: 50%;
}

.content-left-row-2 {
  z-index: 1;

  min-width: 120px;
  float: left;
  padding-top: 50px;
  height: fit-content;

  div {
    height: fit-content;
    min-width: 120px;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;

    h2 {
      font-size: 4em;
      font-weight: 900;
      color: white;
    }
    h3 {
      font-size: 3em;
      font-weight: 300;
      padding-top: 20px;
      color: white;
    }
    p {
      font-size: 1.5em;
      padding-top: 20px;
      color: #6c757d;
    }
  }
}

.row-1 {
  display: flex;
  margin-top: 100px;
}
.row-2 {
  display: flex;
  margin-top: 100px;
}
.since {
  width: 100%;
  height: 200px;
  /* background: white; */
  display: flex;
  align-items: center;
  justify-content: center;
  p {
    color: white;
    font-size: 2em;
    font-weight: 300;
    border-bottom: 2px solid white;
  }
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
</style>
