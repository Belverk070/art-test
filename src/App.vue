<template>
  <h1 class="title">
    SEND<br />
    A REQUEST
  </h1>
  <section class="content">
    <div class="content-wrapper">
      <p class="content__description">
        Leave your contacts and we will contact you as soon as possible
      </p>
      <img class="content__logo" src="./assets/images/logo.svg" alt="Company logo" />
    </div>
    <request-form />
  </section>
  <footer class="footer">
    <p class="footer__author">© 2022 LUXURY RESIDENCE</p>
    <a class="footer__policy-link" href="#">Privacy Policy</a>
  </footer>
</template>

<script>
import RequestForm from './components/RequestForm.vue';

export default {
  name: 'App',
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
  src: url("./assets/fonts/GHEAMariamReg.otf") format("opentype");
}
@font-face {
  font-family: "GHEA Grapalat";
  font-style: normal;
  font-weight: 400;
  src: url("./assets/fonts/GHEAGrpalatReg.otf") format("opentype");
}
#app {
  max-width: 1920px;
  width: 100%;
  background: #21354b;
  padding: 58px 85px 52px;
  color: #eeebe6;
  min-height: 100vh;
  position: relative;
}
.title {
  font-family: "GHEA Mariam";
  font-style: normal;
  font-weight: 400;
  font-size: 66px;
  line-height: 1.1;
  letter-spacing: 0.03em;
  text-transform: uppercase;
  margin-bottom: 52px;
}
.content {
  display: flex;
  justify-content: flex-start;
  width: 100%;
  margin-bottom: 135px;
}
.content-wrapper {
  display: flex;
  flex-direction: column;
  margin-right: 36%;
}
.content__description {
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 1.5;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  margin-bottom: 90px;
  max-width: 200px;
}
.content__logo {
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
.footer__policy-link {
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
.footer__policy-link:hover {
  opacity: 0.6;
  transition: all 0.3s ease-in-out;
}
@media screen and (max-width: 1150px) {
  #app {
    min-width: 320px;
    width: 100%;
    padding: 20px 15px;
  }
}
@media screen and (max-width: 995px) {
  .title {
    font-size: 46px;
  }
  .content-wrapper {
    margin-right: 0;
    gap: 40px;
    justify-content: flex-start;
  }
  .content__description {
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
  .content {
    flex-direction: column;
  }
  .content__description {
    margin-right: 30px;
    max-width: 200px;
    font-size: 14px;
  }
  .content-wrapper {
    margin-bottom: 20px;
  }
}
@media screen and (max-width: 450px) {
  .content-wrapper {
    justify-content: flex-start;
    flex-direction: column-reverse;
    margin-bottom: 45px;
  }
  .content__logo {
    width: 100px;
    height: 26px;
  }
  .content {
    flex-direction: column;
    margin-bottom: 40px;
  }
  .footer {
    justify-content: space-around;
    font-size: 11px;
  }
  .footer__author {
    margin-right: 20px;
  }
}
</style>
