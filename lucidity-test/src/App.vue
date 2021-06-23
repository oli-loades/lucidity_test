<template>
  <div id="app">
    <div class="your-profile">
      <form class="profile-form">
        <p class="title">Your profile</p>
        <div class="flex-container input-row">
          <div class="left-input">
            <label class="input-label text" for="firstname">First name</label>
            <input
              type="text"
              class="text-input text"
              id="firstname"
              v-model="firstName"
            />
          </div>
          <div class="right-input">
            <label class="input-label text" for="lastname">Last name</label>
            <font-awesome-icon class="help" icon="question-circle" />
            <input
              type="text"
              class="text-input text"
              id="lastname"
              v-model="lastName"
            />
          </div>
        </div>
        <div class="input-row">
          <label class="input-label text" for="email">Email Address</label>
          <font-awesome-icon class="help" icon="question-circle" />
          <input
            type="text"
            class="text-input full-width text"
            id="email"
            v-model="emailAddress"
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
        <button class="submit-button button">Save changes</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      firstName: "",
      lastName: "",
      emailAddress: "",
      imageSrc:
        "http://ghost.skillshub.info/content/images/2017/01/profile-girl-square.png",
    };
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
  height: 518px;
  border: 1px solid #d9d2e7;
  box-sizing: border-box;
  border-radius: 4px;
  background: #ffffff;
  padding: 32px;
  margin: 0 auto;
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

.full-width {
  width: 100%;
}

.help {
  color: #d9d2e7;
  float: right;
}

.upload {
  margin-top: 8px;
}
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700&family=Source+Sans+Pro:wght@400;600;700&display=swap");
</style>
