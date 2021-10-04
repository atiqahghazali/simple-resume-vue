<template>
  <Title :text="contactsLabel" />
  <div v-if="email" class="contact-line">
    <img src="@/assets/email.svg" />
    <Paragraph class="contact" :text="email" />
  </div>
  <div v-if="email" class="contact-line">
    <img src="@/assets/linkedin.svg" />
    <Paragraph class="contact" :text="linkedIn" />
  </div>
  <div v-if="email" class="contact-line">
    <img src="@/assets/telegram.png" width="20" height="20"/>
    <Paragraph class="contact" :text="telegram" />
  </div>
  <div v-if="email" class="contact-line">
    <img src="@/assets/github.png" width="20" height="20"/>
    <Paragraph class="contact" :text="github" />
  </div>
</template>

<script>
import Title from "@/components/Title.vue";
import Paragraph from "@/components/Paragraph.vue";

export default {
  name: "Contacts",

  components: { Title, Paragraph },

  computed: {
    currentLanguage() {
      return this.$store.state.currentLanguage;
    },

    contactsLabel() {
      return this.currentLanguage.resumeLabels.contacts;
    },

    contacts() {
      return this.currentLanguage.data.contacts;
    },

    phoneNumber() {
      return this.contacts.phone;
    },

    email() {
      return this.contacts.email;
    },

    linkedIn() {
      return this.contacts.linkedIn;
    },

    telegram() {
      return this.contacts.telegram;
    },

    github() {
      return this.contacts.github;
    },
  },
};
</script>

<style scoped>
.contact-line {
  display: flex;
  margin: 0 auto;
  align-items: center;
}

.contact {
  padding-left: 1em;
  margin: 0.25em;
}
</style>
