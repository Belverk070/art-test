<template>
  <div id="app">
    <h1 class="app__title">
      SEND<br />
      A REQUEST
    </h1>

    <section class="app__content">

      <div class="app__info">
        <p class="app__description">
          Leave your contacts and we will contact you as soon as possible
        </p>
        <img class="app__logo" src="./assets/images/logo.svg" alt="Company logo" />
      </div>

      <request-form />

    </section>

    <footer class="footer">
      <p class="footer__author">© 2022 LUXURY RESIDENCE</p>
      <a class="footer__policy" href="#">Privacy Policy</a>
    </footer>
  </div>
</template>

<script>
import RequestForm from './components/RequestForm.vue';

export default {
  components: { RequestForm },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "GHEA Grapalat";
}

@font-face {
  font-family: "GHEA Mariam";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url("./assets/fonts/GHEAMariamReg.otf") format("opentype");
}

@font-face {
  font-family: "GHEA Grapalat";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url("./assets/fonts/GHEAGrpalatReg.otf") format("opentype");
}

#app {
  max-width: 1920px;
  width: 100%;
  background: #21354b;
  padding: 29px 43px 80px;
  color: #eeebe6;
  min-height: 100vh;
  position: relative;
}

.app__title {
  font-family: "GHEA Mariam";
  font-style: normal;
  font-weight: 400;
  font-size: 66px;
  line-height: 1.1;
  letter-spacing: 0.03em;
  text-transform: uppercase;
  margin-bottom: 52px;
}

.app__content {
  display: flex;
  justify-content: flex-start;
  width: 100%;
  margin-bottom: 145px;
}

.app__info {
  display: flex;
  flex-direction: column;
  margin-right: 36%;
}

.app__description {
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 1.5;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  margin-bottom: 90px;
  max-width: 200px;
}

.app__logo {
  width: 192px;
  height: 47px;
  opacity: 0.2;
}

.footer {
  display: flex;
  justify-content: flex-start;
}

.footer__author {
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 1.5;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  color: #ff69b4;
  margin-right: 208px;
}

.footer__policy {
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 1.5;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  font-style: normal;
  color: #eeebe6;
  text-decoration: none;
  transition: all 0.3s ease-in-out;
}

.footer__policy:hover {
  opacity: 0.6;
  transition: all 0.3s ease-in-out;
}

@media screen and (max-width: 995px) {
  #app {
    min-width: 320px;
    width: 100%;
    padding: 20px 15px;
  }

  .app__title {
    font-size: 46px;
  }

  .app__content {
    flex-direction: column;
  }

  .app__info {
    margin-right: 0;
    gap: 40px;
    margin-bottom: 60px;
    justify-content: center;
  }

  .app__description {
    margin-bottom: 0;
    margin-right: 50px;
    max-width: 300px;
  }

  .footer {
    bottom: 20px;
    left: 15px;
  }
}

@media screen and (max-width: 585px) {
  .app__info {
    justify-content: flex-start;
  }

  .app__description {
    margin-right: 30px;
    max-width: 200px;
    font-size: 14px;
  }
}

@media screen and (max-width: 450px) {
  .app__info {
    align-items: center;
  }

  .app__logo {
    width: 100px;
    height: 26px;
  }

  .footer__author {
    font-size: 11px;
    margin-right: 20px;
  }

  .footer__policy {
    font-size: 11px;
  }
}
</style>
