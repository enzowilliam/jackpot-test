<script>
export default {
  data() {
    return {
      spinning: false,
      digits: [0, 0, 0], // Array de dígitos iniciais
      result: ''
    };
  },
  methods: {
    spin() {
      if (this.spinning) return;

      this.spinning = true;

      const targetNumber = Math.floor(Math.random() * 1000);
      const intervalDuration = 200;
      const totalIterations = 10;
      let currentNumber = 0;

      const interval = setInterval(() => {
        currentNumber += Math.floor(targetNumber / totalIterations);

        for (let i = 0; i < this.digits.length; i++) {
          const digitValue = Math.floor(currentNumber / Math.pow(10, i)) % 10;
          this.digits[i] = digitValue;
        }

        if (currentNumber >= targetNumber) {
          clearInterval(interval);
          this.spinning = false;
        }
      }, intervalDuration);
    }
  }
};
</script>

<template>
  <div class="jackpot">
    <div class="jackpot-wraper">
      <img
        src="../assets/caca-niquel.png"
        alt="caça niquel vermelho cercado com bolinhas amarelas"
      />
      <div class="slot-machine">
        <div class="slot" v-for="(digit, index) in digits" :key="index">
          <div class="digit" :class="{ spinning: spinning }">{{ digit }}</div>
        </div>
      </div>
    </div>
    <div class="spin">
      <button @click="spin" :disabled="spinning">Spin</button>
    </div>
  </div>
</template>

<style>
.jackpot {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}

.jackpot-wraper {
  position: relative;
  margin-top: -1.2rem;
}

.slot-machine {
  display: flex;
  position: absolute;
  top: 40%;
  left: 25%;
}

.slot {
  margin: 0 5px;
  background-color: #ffff;
}

.digit {
  width: 1rem;
  height: 2rem;
  display: flex;
  justify-content: center;

  align-items: center;
  font-size: 24px;
}

.spinning {
  animation: spin 1s infinite;
}

@keyframes spin {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-6.5px);
  }
  100% {
    transform: translateY(0);
  }
}

img {
  width: 10rem;
  height: 10rem;
  margin: 0 auto;
  display: block;
}

button {
  margin: 0 8rem;
  padding: 5px 10px;
  font-size: 16px;
  border-radius: 5px;
  background-color: #332354;
  border: none;
  color: #ffffff;
  cursor: pointer;
}
</style>
