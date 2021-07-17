<template>
  <div class="input-text">
    <div v-if="error" class="input-text__error-line"></div>
    <div class="input-text__content">
      <div v-if="error" class="input-text__error-container">
        <font-awesome-icon icon="exclamation-triangle" />
        <p class="input-text__error-text">{{ error }}</p>
      </div>
      <div>
        <label class="input-text__label" :for="id">{{ label }}</label>
        <font-awesome-icon
          v-if="help"
          class="input-text__help-icon"
          icon="question-circle"
        />
        <input
          type="text"
          :class="dynamicDisabledClass"
          :id="id"
          :value="value"
          :disabled="disabled"
          @input="$emit('input', $event.target.value)"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "InputText",
  props: {
    label: {
      type: String,
      default: "",
    },
    id: {
      type: String,
      required: true,
    },
    value: {
      type: String,
      default: "",
    },
    help: {
      type: String,
    },
    error: {
      type: String,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    dynamicDisabledClass() {
      const baseClasses = "input-text__input";
      return this.disabled
        ? baseClasses + " " + baseClasses + "--disabled"
        : baseClasses;
    },
  },
};
</script>

<style scoped>
.input-text__label {
  display: inline-block;
  font-size: 15px;
  line-height: 21px;
  color: #605871;
  margin-bottom: 4px;
}

.input-text__input {
  background: #ffffff;
  border: 1px solid #b2a6c9;
  box-sizing: border-box;
  border-radius: 4px;
  font-size: 16px;
  line-height: 24px;
  color: #000000;
  height: 40px;
  width: 100%;
  padding: 8px 16px;
  font-weight: 400;
}

.input-text__help-icon {
  color: #d9d2e7;
  float: right;
}

.text-input:hover:not(.disabled) {
  border: 3px solid #9c72f0;
}

.text-input:focus:not(.disabled) {
  border: 3px solid #9c72f0;
}

.input-text__input--disabled {
  background: #f2eff8;
}

.input-text__error-text {
  line-height: 21px;
  margin: 0 0 0 8px;
}

.input-text__error-container {
  display: flex;
  flex-direction: row;
  color: #e0004d;
  align-items: center;
  margin-bottom: 8px;
}

.input-text {
  display: flex;
  flex-direction: row;
  font-family: Source Sans Pro;
  font-style: normal;
  font-weight: 600;
}

.input-text__error-line {
  margin-right: 18px;
  border-left: 6px solid #e0004d;
  min-height: 100%;
}

.input-text__content {
  display: flex;
  flex-direction: column;
  width: 100%;
}
</style>
