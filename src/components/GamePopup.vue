<script>
import Form from '../components/Form.vue';
import texts from '../assets/data.json';
import Jackpot from '../components/Jackpot.vue';

export default {
  components: {
    Form,
    Jackpot
  },
  data() {
    return {
      formData: {},
      popupTexts: texts.gamePopup
    };
  }
};
</script>

<template>
  <div class="game-popup">
    <h2>
      {{ popupTexts.title }}<br /><small>{{ popupTexts.subtitle }}</small>
    </h2>
    <div class="jackpot-style"></div>
    <Jackpot />
    <Form />
  </div>
</template>

<style scoped>
.game-popup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 20rem;
  height: 40rem;
  padding: 20px;
  margin: 0 auto;
  border-radius: 10px;
  background-color: #ffffff;
  z-index: 1000;
}

h2 {
  margin-top: 0;
  text-align: center;
  margin-bottom: 20px;
  color: #332354;
}

h2 small {
  font-weight: normal;
  color: #333339;
}

img {
  width: 10rem;
  height: 10rem;
  margin: 0 auto;
  display: block;
  mix-blend-mode: multiply;
}
</style>
