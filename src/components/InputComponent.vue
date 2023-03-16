<template>
  <div class="input__container">
    <label class="input__label" :for="id">
      {{ inputLabel }}
      <input
        class="input"
        :class="{invalid: invalid}"
        :id="id"
        :placeholder="placeholder"
        :type="type"
        :required="required"
        :value="modelValue"
        @input="updateInput"
        v-if="rangeType"
      />
      <input
        class="input__range"
        :id="id"
        :value="modelValue"
        :style="{ backgroundSize: modelValue + '% 100%' }"
        type="range"
        min="0"
        max="100"
        @input="updateInput"
        v-else
      />
    </label>
    <p class="input__temp input__temp_hot" v-if="!rangeType">HOT</p>
    <p class="input__temp input__temp_cold" v-if="!rangeType">COLD</p>
  </div>
</template>

<script>
export default {
  name: 'InputComponent',
  props: {
    inputLabel: String,
    required: Boolean,
    placeholder: String,
    id: String,
    type: String,
    modelValue: [String, Number],
    invalid: Boolean,
  },
  methods: {
    updateInput(evt) {
      this.$emit('update', evt.target.value);
    },
  },
  computed: {
    rangeType() {
      return this.type !== 'range';
    },
  },
};
</script>

<style scoped>
.input__container {
  display: flex;
  flex-direction: column;
  margin-bottom: 51px;
  position: relative;
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
  margin-bottom: 5px;
}
.input {
  font-style: normal;
  font-weight: 400;
  font-size: 12px;
  line-height: 1.5;
  background-color: transparent;
  border: none;
  border-bottom: 1px solid rgba(238, 235, 230, 0.5);
  color: #eeebe6;
  padding: 3px 0;
}
.invalid {
  border-bottom: 2px solid red;
}
.input:focus-visible {
  outline: none;
}
.input__temp {
  position: absolute;
  top: 48px;
  font-style: normal;
  font-weight: 400;
  font-size: 9px;
  line-height: 150%;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}
.input__temp_hot {
  left: 0;
}
.input__temp_cold {
  right: 0;
}
.input__range {
  appearance: none;
  position: absolute;
  top: 41px;
  left: 0;
  width: 100%;
  height: 1px;
  background: #5baaf9;
  background-image: linear-gradient(#ff69b4, #ff69b4);
  background-size: 50% 100%;
  background-repeat: no-repeat;
}
</style>
