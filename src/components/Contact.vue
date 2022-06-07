<template>
  <div id="contact">
      <form class="contact-form" @submit.prevent="sendEmail">
    <label>Name</label>
    <input type="text" name="user_name">
    <label>Email</label>
    <input type="email" name="user_email">
    <label>Message</label>
    <textarea name="message"></textarea>
    <input type="submit" value="Send" @click="sendEmail">
  </form>
  </div>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
  name: 'Contact',
  props: {
    msg: String
  },
  methods : {
      sendEmail: (e) => {
      emailjs.sendForm('service_pavp8d5', 'template_vctb17y', e.target, 'tI_GYCmxxx1ocbTk6')
        .then((result) => {
            console.log('SUCCESS!', result.status, result.text);
        }, (error) => {
            console.log('FAILED...', error);
        });
  },
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
