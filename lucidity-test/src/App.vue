<template>
  <div id="app">
    <div class="your-profile">
      <form @submit.prevent="submit" class="profile-form">
        <p class="title">Your profile</p>
        <div class="flex-container input-row">
          <div class="left-input">
            <InputText
              label="First name"
              id="Firstname"
              v-model="firstName"
              :error="firstNameError"
              :disabled="disabled"
            />
          </div>
          <div class="right-input">
            <InputText
              label="Last name"
              id="lastname"
              v-model="lastName"
              help="Last name"
              :error="lastNameError"
              :disabled="disabled"
            />
          </div>
        </div>
        <div class="input-row">
          <InputText
            label="Email Address"
            id="email"
            v-model="emailAddress"
            help="Email address"
            :error="emailError"
            :disabled="disabled"
          />
        </div>
        <div>
          <p class="image-text text">Your photo (Recommended size 200px)</p>
          <font-awesome-icon class="help" icon="question-circle" />
          <div class="flex-container upload">
            <img :src="imageSrc" />
            <div class="upload-container">
              <button class="upload-button button">Upload new image</button>
            </div>
          </div>
          <p class="remove-text text">Remove existing image</p>
        </div>
        <button type="submit" :class="dynamicDisabledClass" :disable="disabled">Save changes</button>
        <p v-if="submitted" class="success text">Changes saved successfully</p>
      </form>
    </div>
  </div>
</template>

<script>
import InputText from "./components/InputText";

export default {
  name: "App",
  components: { InputText },
  data() {
    return {
      firstName: "",
      lastName: "",
      emailAddress: "",
      imageSrc:
        "http://ghost.skillshub.info/content/images/2017/01/profile-girl-square.png",
      currentErrors: {
        first: false,
        last:false,
        email:false
      },
      submitted: false,
      disabled: false,
    };
  },
  computed: {
    firstNameError() {
      return this.currentErrors.first ? "Invalid first name" : "";
    },
    lastNameError() {
      return this.currentErrors.last ? "Invalid last name" : "";
    },
    emailError() {
      return this.currentErrors.email ? "Invalid email address" : "";
    },
    dynamicDisabledClass() {
      const baseClasses = "submit-button button";
      return this.disabled ? "disabled-button " + baseClasses : baseClasses;
    }
  },
  methods: {
    submit() {
      const valid = this.validate();
      if (!valid) {
        return;
      } else {
        this.disabled = true;
        setTimeout(() => {
          this.disabled = false;
          this.submitted = true;
        }, 3000);
      }
    },
    validate() {
      this.currentErrors.first = this.validateLength(this.firstName);
      this.currentErrors.last = this.validateLength(this.lastName);
      this.currentErrors.email =
        this.validateLength(this.emailAddress) || this.validateEmail();
      return !this.currentErrors.first && !this.currentErrors.last && !this.currentErrors.email;
    },
    validateLength(val) {
      return val.length < 2 || val.legnth > 255;
    },
    validateEmail() {
      const emailRegex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return !emailRegex.test(this.emailAddress.toLowerCase());
    },
  },
};
</script>

<style>
html,
body,
#app {
  margin: 0;
  padding: 0;
  height: 100%;
}

.text {
  font-family: Source Sans Pro;
  font-style: normal;
  font-weight: 600;
}

.your-profile {
  background: #e5e5e5;
  padding-top: 40px;
  height: 100%;
}

.profile-form {
  width: 664px;
  border: 1px solid #d9d2e7;
  box-sizing: border-box;
  border-radius: 4px;
  background: #ffffff;
  padding: 32px;
  margin: 0 auto;
}

.title {
  font-family: Montserrat;
  font-style: normal;
  font-weight: bold;
  font-size: 15px;
  line-height: 25px;
  color: #000000;
  margin-bottom: 19px;
  margin-top: 0;
}

.image-text {
  font-size: 15px;
  line-height: 21px;
  color: #605871;
  margin-top: 0;
  margin-bottom: 8px;
  display: inline;
}

.remove-text {
  font-size: 15px;
  line-height: 27px;
  color: #e0004d;
  margin-top: 8px;
  margin-bottom: 32px;
}

img {
  border-radius: 50%;
  min-width: 80px;
  min-height: 80px;
  max-width: 80px;
  max-height: 80px;
  margin-right: 32px;
}

.upload-container {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  background: #f7f5fc;
  border-radius: 4px;
}

.flex-container {
  display: flex;
}

.button {
  font-family: Montserrat;
  font-style: normal;
  font-weight: bold;
  font-size: 14px;
  text-align: center;
}

.upload-button {
  width: 162px;
  height: 40px;
  line-height: 26px;
  color: #0f002e;
  background: #ffffff;
  border: 1px solid #d9d2e7;
  box-sizing: border-box;
  box-shadow: 0px 2px 3px rgba(0, 0, 0, 0.08);
  border-radius: 4px;
}

.submit-button {
  background: linear-gradient(111.77deg, #e92a6c 0%, #2e008b 100%);
  box-shadow: 0px 2px 3px rgba(0, 0, 0, 0.15);
  border-radius: 4px;
  line-height: 24px;
  color: #ffffff;
  border-color: transparent;
  width: 132px;
  height: 40px;
}

.input-row {
  margin-bottom: 32px;
}

.left-input {
  margin-right: 16px;
  flex-basis: 50%;
}

.right-input {
  flex-basis: 50%;
}

.upload {
  margin-top: 8px;
}

.success {
  line-height: 27px;
  color: green;
  margin-bottom: 0;
}

.disabled-button {
  background: #f2eff8;;
  cursor: not-allowed;
  color: grey;
}
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&family=Source+Sans+Pro:wght@400;600;700&display=swap");
</style>
