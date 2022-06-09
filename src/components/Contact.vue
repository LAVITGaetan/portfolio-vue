<template>
  <div id="contact">
    <form class="contact-form" @submit.prevent="sendEmail">
      <div class="form-group">
        <label class="form-label">Name</label>
        <input class="form-input" type="text" name="user_name" />
      </div>
      <div class="form-group">
        <label class="form-label">Email</label>
        <input class="form-input" type="email" name="user_email" />
      </div>
      <div class="form-group">
        <label class="form-label">Message</label>
        <textarea class="form-textarea" name="message"></textarea>
      </div>
      <button
        class="form-btn btn btn0"
        type="submit"
        value="Envoyer"
        @click="sendEmail"
      >
      <p class="form-btn-text">Envoyer</p>
      
      <div class="form-btn-design"></div>
      </button>
    </form>
  </div>
</template>

<script>
import emailjs from "emailjs-com";

export default {
  name: "Contact",
  props: {
    msg: String,
  },
  methods: {
    sendEmail: (e) => {
      emailjs
        .sendForm(
          "service_pavp8d5",
          "template_vctb17y",
          e.target,
          "tI_GYCmxxx1ocbTk6"
        )
        .then(
          (result) => {
            console.log("SUCCESS!", result.status, result.text);
          },
          (error) => {
            console.log("FAILED...", error);
          }
        );
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form-group {
  max-width: 300px;
  min-width: 300px;
  display: flex;
  flex-direction: column;
  margin: 1em auto;
}

.form-label {
  padding-bottom: 0.5em;
  font-size: 17px;
  color: var(--colorLight);
}

.form-input {
    max-width: 300px;
  min-width: 300px;
  padding: .7em 1.4em;
}

.form-textarea {
  max-width: 300px;
  min-width: 300px;
  min-height: 120px;
  max-height: 500px;
}

.form-btn {
  margin: 2em auto .5em auto;
  outline: none;
  border: none;
  display: block;
  position: relative;
}

.form-btn::before {
  transition: .4s ease;
  position: absolute;
  content: "";
  width : 0%;
  height: 100%;
  top: 0;
  left: 0;
  background: var(--colorDarkLighter);
  clip-path: circle(20% at 0 0);
  z-index: 10;
cursor: pointer;
}

.form-btn-text {
  z-index: 20;
}

.form-btn:hover::before {
  transition: .4s ease;
  width: 100%;
  height: 100%;
clip-path: circle(20.7% at 98% 4%);
}
</style>
