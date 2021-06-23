<template>
  <div class="row">
    <div v-if="error" class="error-line"></div>
    <div class="col">
      <div v-if="error" class="error-container">
        <font-awesome-icon icon="exclamation-triangle" />
        <p class="error-text text">{{ error }}</p>
      </div>
      <div>
        <label class="input-label text" :for="id">{{ label }}</label>
        <font-awesome-icon v-if="help" class="help" icon="question-circle" />
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
      const baseClasses = "text-input text";
      return this.disabled ? baseClasses + " disabled" : baseClasses;
    },
  },
};
</script>

<style>
.text {
  font-family: Source Sans Pro;
  font-style: normal;
  font-weight: 600;
}

.input-label {
  font-size: 15px;
  line-height: 21px;
  color: #605871;
  margin-bottom: 4px;
}

.text-input {
  background: #ffffff;
  border: 1px solid #b2a6c9;
  box-sizing: border-box;
  border-radius: 4px;
  font-size: 16px;
  line-height: 24px;
  color: #000000;
  height: 40px;
  width: 100%;
}

.help {
  color: #d9d2e7;
  float: right;
}

.text-input:hover:not(.disabled) {
  border: 3px solid #9c72f0;
}

.disabled {
  background: #f2eff8;
}

.error-text {
  line-height: 21px;
  margin: 0 0 0 8px;
}

.error-container {
  display: flex;
  flex-direction: row;
  color: #e0004d;
  align-items: center;
  margin-bottom: 8px;
}

.row {
  display: flex;
  flex-direction: row;
}

.error-line {
  margin-right: 18px;
  border-left: 6px solid #e0004d;
  min-height: 100%;
}

.col {
  display: flex;
  flex-direction: column;
  width: 100%;
}
</style>
