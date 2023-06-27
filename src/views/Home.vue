<script>
import GamePopup from '../components/GamePopup.vue';
import VideoPopup from '../components/VideoPopup.vue';

export default {
  components: {
    GamePopup,
    VideoPopup
  },
  data() {
    return {
      popupVisible: false,
      popupComponent: null
    };
  },
  methods: {
    openGamePopup() {
      this.popupVisible = true;
      this.popupComponent = 'GamePopup';
    },

    openVideoPopup() {
      this.popupVisible = true;
      this.popupComponent = 'VideoPopup';
      console.log('openVideoPopup');
    },

    closePopup() {
      this.popupVisible = false;
    }
  }
};
</script>
<template>
  <div class="container">
    <div class="header">
      <h1>Experimente a emoção do Jackpot</h1>
    </div>
    <div class="content">
      <div class="popup-overlay" v-if="popupVisible" @click="closePopup"></div>
      <component :is="popupComponent" v-if="popupVisible"></component>
      <div class="options">
        <div class="button" @click="openGamePopup">
          <h2>Caça Niquel</h2>
          <p>
            Explore a empolgante aventura dos jogos de caça-níquel e mergulhe em
            um mundo repleto de diversão e chances de ganhar. Com uma ampla
            variedade de temas emocionantes e símbolos coloridos, nossos jogos
            de caça-níquel oferecem uma experiência envolvente e cheia de
            adrenalina. Gire os rolos, desvende combinações vencedoras e
            aproveite os recursos especiais para desbloquear rodadas de bônus e
            prêmios incríveis. Entre na diversão e experimente a emoção dos
            jogos de caça-níquel hoje mesmo!
          </p>
          <div class="dice">
            <svg
              stroke="currentColor"
              fill="currentColor"
              stroke-width="0"
              viewBox="0 0 16 16"
              height="1em"
              width="1em"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M13 1a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V3a2 2 0 0 1 2-2h10zM3 0a3 3 0 0 0-3 3v10a3 3 0 0 0 3 3h10a3 3 0 0 0 3-3V3a3 3 0 0 0-3-3H3z"
              ></path>
              <path
                d="M5.5 4a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm8 8a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0z"
              ></path>
            </svg>
          </div>
        </div>
        <div class="button" @click="openVideoPopup">
          <h2>Tutorial</h2>
          <p>
            Um jackpot é um prêmio acumulado em um jogo de azar ou cassino que
            aumenta progressivamente à medida que os jogadores apostam.
            Geralmente, uma pequena porcentagem de cada aposta é adicionada ao
            prêmio, resultando em um valor cada vez maior. O jackpot é ganho
            quando um jogador atinge uma combinação específica ou condição
            pré-determinada no jogo, clique para ver um video sobre.
          </p>
          <div class="video-svg">
            <svg
              stroke="currentColor"
              fill="currentColor"
              stroke-width="0"
              viewBox="0 0 24 24"
              height="1em"
              width="1em"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path d="M4 8H2v12a2 2 0 0 0 2 2h12v-2H4z"></path>
              <path
                d="M20 2H8a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V4a2 2 0 0 0-2-2zm-9 12V6l7 4z"
              ></path>
            </svg>
          </div>
        </div>
      </div>
    </div>
    <div class="footer-container">
      <img class="logo" src="../assets/logo.png" alt="logo da popconvert" />
    </div>
  </div>
</template>

<style>
.container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100vh;
}

h1 {
  margin-left: 1rem;
  color: #ffffff;
}

.content {
  display: flex;
  justify-content: center;
  align-items: center;
}

.options {
  display: flex;
  width: 100%;
}

.button:first-child {
  border-left-width: 0;
}

.button:last-child {
  border-left-width: 0;
  border-right-width: 0;
}

.button {
  color: #e5e5e5;
  position: relative;
  padding: 0.5rem 1rem;
  width: 100%;
  height: 30rem;
  background-color: #202024;
  border: 1px solid #6e6e6e;
  cursor: pointer;
}

.button:hover {
  background-color: #333339;
  transform: scaleY(1);
  transform-origin: bottom left;
}

.button::before {
  transform: scaleY(1);
  transform-origin: bottom right;
}

.button:hover::before {
  background-color: #202024;
  transform: scaleY(0);
  transform-origin: bottom left;
}

.button::before {
  content: ' ';
  display: block;
  position: absolute;
  right: 0;
  bottom: 1;
  left: 0;
  inset: 0 0 0 0;
  background: #757575;
  z-index: -1;
  transition: transform 1s ease;
}

svg {
  width: 5rem;
  height: 10rem;
}

p {
  font-size: 1rem;
}

.dice {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
}

.video-svg {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
}

@media screen and (max-width: 768px) {
  .content {
    flex-direction: column;
    height: 100%;
  }

  .options {
    flex-direction: column;
    height: 100%;
    width: 90%;
  }
}

.popup-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 999;
}

.footer-container {
  padding: 1rem;
}

.logo {
  margin-right: 0;
  margin-left: auto;
  width: 15rem;
  height: auto;
  filter: grayscale(100%) brightness(0);
  opacity: 0.5;
}
</style>
