<template>
  <div>
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
export default {};
</script>

<style lang="scss" scoped>
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