<script>
import Form from '../components/Form.vue';
import texts from '../assets/data.json';

export default {
  components: {
    Form
  },
  data() {
    return {
      formData: {},
      popupTexts: texts.videoPopup
    };
  }
};
</script>

<template>
  <div class="video-popup">
    <h2>
      {{ popupTexts.title }}<small>{{ popupTexts.subtitle }}</small>
    </h2>
    <div class="video">
      <iframe
        width="250"
        height="170 "
        src="https://www.youtube.com/embed/FAhm7A7jQro"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        allowfullscreen
      ></iframe>
    </div>
    <Form />
  </div>
</template>

<style scoped>
.video-popup {
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

.video {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 0.5rem;
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
  display: block;
}

img {
  width: 100px;
  height: 100px;
  margin: 0 auto;
  display: block;
  mix-blend-mode: multiply;
}
</style>
