<template>
  <form @submit.prevent class="form">
    <div class="input__container">
      <label class="input__label" for="input-name">
        NAME
        <input
          class="input"
          name="input-name"
          id="input-name"
          type="text"
          v-model="formData.nameValue"
          required
        />
      </label>

      <label class="input__label" for="input-phone"
        >PHONE
        <input
          class="input"
          name="input-phone"
          id="input-phone"
          type="text"
          :value="formData.phoneValue"
          v-imask="mask"
          :pattern="validationPhoneRegex"
          @accept="validatePhoneNumber"
          required
        />
      </label>

      <label class="input__label" for="input-temp">
        TEMP
        <input
          class="input__range"
          name="input-temp"
          id="input-temp"
          type="range"
          v-model="formData.temperatureValue"
          :style="{ backgroundSize: formData.temperatureValue + '% 100%' }"
        />
      </label>

      <label class="input__label" for="input-comments">
        COMMENTS
        <input
          class="input"
          name="input-comments"
          id="input-comments"
          type="text"
          v-model="formData.commentsValue"
        />
      </label>
    </div>

    <div class="form__action-wrapper">
      <button class="form__submit" type="submit" @click="handleSubmit">Call me</button>
      <p class="form__policy">
        By pressing “Send” button I agree with
        <a class="form__policy-link" href="#">Privacy Policy</a>
      </p>
    </div>
  </form>
</template>

<script>
import { IMaskDirective } from 'vue-imask';

export default {
  name: 'RequestForm',
  data() {
    return {
      formData: {
        nameValue: null,
        phoneValue: null,
        commentsValue: null,
        temperatureValue: 30,
      },
      validationPhoneRegex: '^((8|\\+7)[\\- ]?)?(\\(?\\d{3}\\)?[\\- ]?)?[\\d\\- ]{10}$',
      mask: {
        mask: '{+7}{ (}000{) }000{-}00{-}00',
        lazy: true,
      },
    };
  },
  directives: {
    imask: IMaskDirective,
  },
  methods: {
    validatePhoneNumber(evt) {
      const maskRef = evt.detail;
      this.formData.phoneValue = maskRef.value;
    },
    handleSubmit() {
      const pattern = new RegExp(this.validationPhoneRegex);
      if (pattern.test(this.formData.phoneValue) && this.formData.nameValue) {
        console.log(JSON.parse(JSON.stringify(this.formData)));
        this.formData.nameValue = '';
        this.formData.phoneValue = '';
        this.formData.commentsValue = '';
      } else {
        console.log('Необходимо заполнить форму.');
      }
    },
  },
};
</script>

<style scoped>
.form__policy-link {
  color: #ff69b4;
  transition: all 0.3s ease-in-out;
  cursor: pointer;
}
.form__policy-link:hover {
  color: #ff0080;
  transition: all 0.3s ease-in-out;
}
.form {
  width: 538px;
  padding-top: 40px;
}
.form__action-wrapper {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
  padding-top: 70px;
}
.form__submit {
  border: 1px solid #eeebe6;
  border-radius: 500px;
  background-color: transparent;
  color: #eeebe6;
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 1.3;
  text-align: center;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  min-width: 180px;
  height: 56px;
  margin-right: 72px;
  transition: all 0.3s ease-in-out;
  cursor: pointer;
}
.form__submit:hover {
  opacity: 0.5;
  transition: all 0.3s ease-in-out;
}
.form__policy {
  max-width: 205px;
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 1.5;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}
.input__container {
  display: flex;
  flex-direction: column;
  margin-bottom: 45px;
  gap: 49px;
}
.input__label {
  display: flex;
  flex-direction: column;
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 1.5;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  margin-bottom: 10px;
}
.input {
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 1.5;
  text-transform: uppercase;
  background-color: transparent;
  width: 100%;
  border: none;
  border-bottom: 1px solid rgba(238, 235, 230, 0.5);
  color: #eeebe6;
  padding: 3px 0;
}
.input:focus-visible {
  outline: none;
}
.input__range {
  appearance: none;
  top: 15px;
  font-size: 9px;
  color: white;
  text-transform: uppercase;
  position: relative;
  top: 5px;
  left: 0;
  width: 100%;
  height: 1px;
  background: #5baaf9;
  background-image: linear-gradient(#ff69b4, #ff69b4);
  background-size: 50% 100%;
  background-repeat: no-repeat;
}
.input__range::before {
  content: "hot";
  position: absolute;
  top: 10px;
  left: 0;
}
.input__range:after {
  content: "cold";
  position: absolute;
  top: 10px;
  right: 0;
}
input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  box-sizing: content-box;
  width: 1px;
  height: 1px;
  scale: 13;
  margin: 5px;
  border-radius: 50%;
  background-color: #b6a16b;
  background-clip: padding-box;
  border: 2px solid transparent;
  cursor: pointer;
}
@media screen and (max-width: 995px) {
  .form__action-wrapper {
    justify-content: space-around;
  }
  .form {
    padding-top: 0px;
  }
}
@media screen and (max-width: 585px) {
  .form {
    width: 100%;
  }
}
@media screen and (max-width: 450px) {
  .form__action-wrapper {
    flex-direction: column;
    align-items: start;
    padding-top: 30px;
  }
  .form__submit {
    width: 100%;
    margin-right: 0;
    margin-bottom: 40px;
  }
  .form__policy {
    max-width: 100%;
    text-align: center;
  }
}
</style>
