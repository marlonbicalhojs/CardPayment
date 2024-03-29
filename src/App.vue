<template>
  <div class="container">
    <div id="card-app">
      <Card ref="functionRef" :card-number="cardNumber" :card-name="cardName" :cvv-number="cvvNumber" :valores-selecionados="valoresSelecionados"/>
    </div>
    <div id="all-inputs">
      <Inputs id="first-input" class="number-input" label="Numero do Cartão" type="text" v-model="cardNumber" @input="formatCardNumber"/>
      <Inputs id="second-input" label="Nome do Cartão" type="text" v-model="cardName"/>

      <div class="junction-line">
        <DateInput class="number-input" @valoresSelecionados="capturarValores"/>
        <Inputs id="cvv-input" class="number-input" label="CVV" type="Number" @focus="especFunc" @blur="especFunc" v-model="cvvNumber"/>
      </div>

      <div id="submit">
        <Inputs id="submit-Inputs" type="submit"/>
      </div>

    </div>
  </div>
</template>

<script>
  import Inputs from './components/input.vue';
  import Card from './components/card.vue';
  import DateInput from './components/date.vue';

  export default {
    name: 'App',
    components: {
        Inputs,
        Card,
        DateInput
    },
    data:() => ({
      cardNumber: '',
      cardName:'',
      cvvNumber:'',
      dateNumber:'',
      valoresSelecionados: {
        mes: '',
        ano: ''
      }
    }),
    methods: {
      especFunc() {
        this.$refs.functionRef.flipCard();
      },

      consoleDate() {
        console.log(this.dateNumber)
      },

      capturarValores(valores) {
      this.valoresSelecionados = { ...this.valoresSelecionados, ...valores };
      },

      formatCardNumber(event) {
      
      let inputValue = event.target.value;
      let sanitizedValue = inputValue.replace(/\s/g, '');
      let numericValue = sanitizedValue.replace(/\D/g, '').slice(0, 16);

      let formattedValue = '';
      for (let i = 0; i < numericValue.length; i++) {
        if (i > 0 && i % 4 === 0) {
          formattedValue += ' ';
        }
        formattedValue += numericValue[i];
      }
      this.cardNumber = formattedValue;
      },

      tradeLogo(){
        
      }
    }
  }
</script>

<style>
html {
  display: flex;
  height: 100%;
  align-items: center;
  justify-content: center;
  background-color: #484d50;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: white;
  padding-bottom: 8px;
  padding-left: 20px;
  padding-right: 20px;
  border-radius: 8px;
  box-shadow: 0px 4px 24px #aaa;
  position: relative;
}

#submit input {
  width: 100%;
  height: 40px;
  border-radius: 4px;
  border: none;
  background-color: #1553da;
  color: white;
  cursor: pointer;
  margin-top: 8px;
}

.junction-line {
  display: flex;
  height: 52px;
  margin-bottom: 20px;
}

#cvv-input{
  display: flex;
  width: 120px;
  height: 100%;
}

#all-inputs{
  margin-top: 136px;
}

#card-app{
  position: absolute;
  top: -24%;
}

#first-input label, #second-input label, #cvv-input label, .number-input label{
  padding-left: 2px;
  padding-bottom: 2px;
}
</style>