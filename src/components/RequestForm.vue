<template>
  <form class="app__form">
    <input-component
      :inputLabel="'NAME'"
      :id="'name'"
      :type="'text'"
      :required="true"
      :modelValue="formData.nameValue"
      @update="updateNameValue"
    />
    <input-component
      :inputLabel="'PHONE'"
      :id="'phone'"
      :type="'tel'"
      :required="true"
      :invalid="!isValidPhoneNumber"
      :modelValue="formData.phoneValue"
      :placeholder="formData.phonePlaceholder"
      @keyup="validatePhoneNumber"
      @update="updatePhoneValue"
    />
    <input-component
      :inputLabel="'TEMP'"
      :id="'temp'"
      :type="'range'"
      :modelValue="formData.temperatureValue"
      @update="updateTemperatureValue"
    />
    <input-component
      :inputLabel="'COMMENTS'"
      :id="'comments'"
      :type="'text'"
      :required="false"
      :modelValue="formData.commentsValue"
      @update="updateCommentsValue"
    />

    <div class="app__form-btn-container">
      <button class="app__form-btn" type="submit" @click.prevent="handleSubmit">Call me</button>
      <p class="app__form-policy">
        By pressing “Send” button I agree with
        <a class="app__form-policy_link" href="#">Privacy Policy</a>
      </p>
    </div>
    <p class="invalid-warning" v-if="!isValidPhoneNumber">Некорректный номер телефона!</p>
  </form>
</template>

<script>
import InputComponent from './InputComponent.vue';

export default {
  name: 'RequestForm',
  components: { InputComponent },
  data() {
    return {
      formData: {
        nameValue: null,
        phoneValue: null,
        phonePlaceholder: 'Например: +79991234567',
        commentsValue: null,
        temperatureValue: 30,
      },
      isValidPhoneNumber: true,
    };
  },
  methods: {
    validatePhoneNumber() {
      const validationRegex = /^\+?7(\d{10})$/;
      if (this.formData.phoneValue.match(validationRegex)) {
        this.isValidPhoneNumber = true;
      } else {
        this.isValidPhoneNumber = false;
      }
    },
    updateNameValue(value) {
      this.formData.nameValue = value;
    },
    updatePhoneValue(value) {
      this.formData.phoneValue = value;
    },
    updateTemperatureValue(value) {
      this.formData.temperatureValue = value;
    },
    updateCommentsValue(value) {
      this.formData.commentsValue = value;
    },
    handleSubmit() {
      if (this.formData.nameValue !== null && this.isValidPhoneNumber) {
        console.log(JSON.parse(JSON.stringify(this.formData)));
      } else {
        console.log('Необходимо заполнить форму.');
      }
    },
  },
};
</script>

<style scoped>
.app__form-policy_link {
  color: #ff69b4;
  transition: all 0.3s ease-in-out;
  cursor: pointer;
}
.app__form-policy_link:hover {
  color: #ff0080;
  transition: all 0.3s ease-in-out;
}
.app__form {
  /* width: 538px; */
  padding-top: 40px;
}
.app__form-btn-container {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
  padding-top: 70px;
}
.app__form-btn {
  border: 1px solid #eeebe6;
  border-radius: 100px;
  background-color: transparent;
  color: #eeebe6;
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 1.3;
  text-align: center;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  padding: 20px 60px;
  margin-right: 72px;
  transition: all 0.3s ease-in-out;
  cursor: pointer;
}
.app__form-btn:hover {
  opacity: 0.7;
  transition: all 0.3s ease-in-out;
}
.app__form-policy {
  max-width: 205px;
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  line-height: 1.5;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}
.invalid-warning {
  color: red;
  font-size: 20px;
}

@media screen and (max-width: 995px) {
  .app__form-btn-container {
    justify-content: space-around;
  }
}

@media screen and (max-width: 585px) {
  .app__form {
    width: 100%;
  }
}

@media screen and (max-width: 450px) {
  .app__form-btn-container {
    flex-direction: column;
    align-items: start;
  }
  .app__form-btn {
    width: 100%;
    margin-right: 0;
    margin-bottom: 20px;
  }
  .app__form-policy {
    max-width: 90%;
    text-align: center;
  }
}
</style>
