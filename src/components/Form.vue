<script>
import texts from '../assets/data.json'

export default {
  data() {
    return {
      formData: {},
      popupTexts: texts.gamePopup
    };
  },
  methods: {
    submitForm() {
      // Lógica para enviar os dados do formulário
    }
  }
};
</script>

<template>
  <div class="form-container">
    <form>
      <div class="inputs">
        <div class="group">
          <input type="text" :id="popupTexts.fields[0].name" required v-model="formData.email" />
          <span class="highlight"></span>
          <span class="bar"></span>
          <label>{{ popupTexts.fields[0].label }}</label>
        </div>

        <div class="group">
          <input type="text" :id="popupTexts.fields[1].name" required v-model="formData.name" />
          <span class="highlight"></span>
          <span class="bar"></span>
          <label>{{ popupTexts.fields[1].label }}</label>
        </div>
        <div class="group">
          <input type="text" :id="popupTexts.fields[2].name" required v-model="formData.phone" />
          <span class="highlight"></span>
          <span class="bar"></span>
          <label>{{ popupTexts.fields[2].label }}</label>
        </div>
      </div>
      <div class="group">
        <label :for="popupTexts.fields[3].name">{{ popupTexts.fields[3].label }}</label>
        <div class="select-wrapper">
          <select :id="popupTexts.fields[3].name" v-model="formData.gender">
            <option value="" disabled selected hidden>Selecione</option>
            <option v-for="option in popupTexts.fields[3].options" :key="option.value" :value="option.value">{{ option.label }}</option>
          </select>
        </div>
      </div>
      <div class="checkbox">
        <input type="checkbox" :id="popupTexts.fields[4].name" v-model="formData.consent" />
        <label :for="popupTexts.fields[4].name">{{ popupTexts.fields[4].label }}</label>
      </div>
      <button class="Formbutton" @click="submitForm">{{ popupTexts.submitButton }}</button>
    </form>
  </div>
</template>


<style scoped>
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.group {
  position: relative;
  margin-bottom: 1.5rem;
}

.checkbox {
  display: flex;
  margin-right: 10rem;
  justify-content: center;
  align-items: center;
  margin-bottom: 2rem;
}

input {
  font-size: 18px;
  padding: 10px 10px 10px 5px;
  display: flex;
  border: none;
  width: 100%;
  border-bottom: 1px solid #757575;
}

input:focus {
  outline: none;
}

.inputs label {
  color: #999;
  font-size: 18px;
  font-weight: normal;
  position: absolute;
  pointer-events: none;
  left: 5px;
  top: 10px;
  transition: 0.2s ease all;
}

input:focus ~ label,
input:valid ~ label {
  top: -20px;
  font-size: 14px;
  color: #332354;
}

.bar {
  position: relative;
  display: block;
  width: 18rem;
}

.bar:before,
.bar:after {
  content: '';
  height: 2px;
  width: 0;
  bottom: 1px;
  position: absolute;
  background: #332354;
  transition: 0.2s ease all;
}

.bar:before {
  left: 50%;
}

.bar:after {
  right: 50%;
}

input:focus ~ .bar:before,
input:focus ~ .bar:after {
  width: 50%;
}

.highlight {
  position: absolute;
  height: 60%;
  width: 100px;
  top: 25%;
  left: 0;
  pointer-events: none;
  opacity: 0.5;
}

input:focus ~ .highlight {
  -webkit-animation: inputHighlighter 0.3s ease;
  -moz-animation: inputHighlighter 0.3s ease;
  animation: inputHighlighter 0.3s ease;
}

@-webkit-keyframes inputHighlighter {
  from {
    background: #332354;
  }
  to {
    width: 0;
    background: transparent;
  }
}

@-moz-keyframes inputHighlighter {
  from {
    background: #332354;
  }
  to {
    width: 0;
    background: transparent;
  }
}

@keyframes inputHighlighter {
  from {
    background: #332354;
  }
  to {
    width: 0;
    background: transparent;
  }
}

.select-wrapper {
  position: relative;
  width: 300px;
}

.select-wrapper select {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  font-size: 18px;
  padding: 10px 5px;
  display: block;
  width: 100%;
  border: none;
  border-bottom: 1px solid #757575;
  background: transparent;
  cursor: pointer;
  z-index: 1;
}

.select-wrapper:after {
  content: '\25BC';
  position: absolute;
  color: #999;
  top: 50%;
  right: 0;
  padding: 0 5px;
  pointer-events: none;
  transform: translateY(-50%);
}

.select-wrapper select:focus {
  outline: none;
}

.select-wrapper label {
  color: #999;
}

.Formbutton {
  margin: 0 10px;
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 5px;
  background-color: #332354;
  border: none;
  color: #ffffff;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  cursor: pointer;
}

.button:hover {
  background-color: #4052a5;
}
</style>
