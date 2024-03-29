<template>
    <div class="flip" id="card">

        <div class="face" id="front">
            <div id="one-line">
                <div class="logo-bandeira">
                    <div><img v-if="showMasterCard" id="mastercard" src="../assets/mastercard.png" alt=""></div>
                    <div><img v-if="showVisa" id="visa" src="../assets/visa1.png" alt=""></div>
                    <div><img v-if="showAmex" id="amex" src="../assets/american1.png" alt=""></div>
                    <div><img v-if="showDiscover" id="discover" src="../assets/discover1.png" alt=""></div>
                    <div><img v-if="showElo" id="elo" src="../assets/Elo.png" alt=""></div>
                    <div><img v-if="showHipercard" id="hipercard" src="../assets/hipercard.png" alt=""></div>
                </div>
            </div>
            <div id="two-line">
                <div id="imgs-cpap">
                    <div id="chip-img"></div>
                    <div id="apr-img"></div>
                </div>
                <div id="container-number">
                    <p id="numberIn-Card">{{ cardNumber}}</p>
                </div>
            </div>
            <div id="three-line">
                <div id="container-name">
                    <label for="nameIn-Card">Nome do Cartão</label>
                    <p id="nameIn-Card">{{ cardName}}</p>
                </div>
                <div id="container-expires">
                    <label for="expiresVisor">Expiração</label>
                    <p id="expiresVisor">{{ valoresSelecionados.mes || 'MM' }}/{{ valoresSelecionados.ano || 'YY'}}</p>
                </div>
            </div>
        </div>

        <div class="face" id="back">
            <div class="allBlack"></div>
            <div id="end-back">
                <label id="labelBack" for="container-cvv">CVV</label>
                <div id="conteiner-cvv">
                <p id="cvvIn-Card">{{ cvvNumber || '###' }}</p>
            </div>
            </div>
            <div class="logo-bandeira-back">
                    <div><img v-if="showMasterCard" id="mastercard" src="../assets/mastercard.png" alt=""></div>
                    <div><img v-if="showVisa" id="visa" src="../assets/visa1.png" alt=""></div>
                    <div><img v-if="showAmex" id="amex" src="../assets/american1.png" alt=""></div>
                    <div><img v-if="showDiscover" id="discover" src="../assets/discover1.png" alt=""></div>
                    <div><img v-if="showElo" id="elo" src="../assets/Elo.png" alt=""></div>
                    <div><img v-if="showHipercard" id="hipercard" src="../assets/hipercard.png" alt=""></div>
                </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    methods: {
        flipCard() {
            const card = document.querySelector('#card');
            card.classList.toggle('flip')
        },
    }, 
    props: {
        cardNumber: '',
        cardName: '',
        cvvNumber: '',
        valoresSelecionados: {
            mes: '',
            ano: ''
        }
    },
    computed: {
    showMasterCard() {
      return (
            this.cardNumber.startsWith('51') ||
            this.cardNumber.startsWith('52') ||
            this.cardNumber.startsWith('53') ||
            this.cardNumber.startsWith('54') ||
            this.cardNumber.startsWith('55'));
    },
    showVisa(){
        return (
            this.cardNumber.startsWith('4'));
    },
    showAmex(){
        return (
            this.cardNumber.startsWith('34') ||
            this.cardNumber.startsWith('37'));
    },
    showDiscover(){
        return (
            this.cardNumber.startsWith('6011') ||
            this.cardNumber.startsWith('6221') ||
            this.cardNumber.startsWith('644') ||
            this.cardNumber.startsWith('65'));
    },
    showElo(){
        return (
            this.cardNumber.startsWith('6363') ||
            this.cardNumber.startsWith('6362') ||
            this.cardNumber.startsWith('6504') ||
            this.cardNumber.startsWith('5067') ||
            this.cardNumber.startsWith('5041'));
    },
    showHipercard(){
        return (
            this.cardNumber.startsWith('6062'));
    },
  }

}
</script>

<style>
.face {
    display: flex;
    box-shadow: 0px 12px 24px 8px #aaa;
    color: white;
    position: absolute;
    width: 320px;
    height: 200px;
    border-radius: 10px;
    box-sizing: border-box;
    padding: 12px;
    
}

#card{
    display: flex;
    justify-content: center;
    transform-style: preserve-3d;
    transition: all 1.5s;
}

#front{
    background-image: url('../assets/fundocinza2.jpg');
    background-size: cover;
    transform: rotateY(180deg);
    backface-visibility: hidden;
    display: flex;
    flex-direction: column;
}

#back{
    display: flex;
    flex-direction: column;
    background-image: url('../assets/fundobranco.jpg');
    background-size: 400px 200px;
    backface-visibility: hidden;
}

.flip {
    transform: rotateY(180deg); 
}

#one-line, #two-line, #three-line{
    flex: 1;
}

#three-line {
    display: flex;
    justify-content: space-between;
}

#three-line{
    align-items: end;
}

#two-line{
    display: flex;
    justify-content: center;
    flex-direction: column;
}

#imgs-cpap{
    display: flex;
}

#chip-img{
    width: 50px;
    height: 50px;
    background-size: cover;
    background-image: url('../assets/chip-cartao.png');
}

#apr-img{
    background-image: url('../assets/aproximação.png');
    background-size: cover;
    width: 45px;
    height: 45px;
}

label{
    color: black;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: bold;
}

#expiresVisor, #nameInCard{
    margin: none;
}

#nameIn-Card{
    color: black;
}

#expiresVisor {
    color: black;
}

#container-name{
    padding-left: 8px;
}

#container-expires{
    display: flex;
    flex-direction: column;
    align-items: center;
}

#cvvIn-Card{
    color: black;
}

#numberIn-Card{
    color: black;
    padding-left: 8px;
    padding-bottom: 8px;
}

p{
    margin-top: 0px;
    margin-bottom: 0px;
    font-size: 12px;
    font-weight: bold;
}

.logo-bandeira{
    display: flex;
    justify-content: center;
    align-items: center;
}

#mastercard{
    height: 30px;
    width: 40px;
}
#visa{
    height: 24px;
    width: 40px;
}
#discover{
    height: 20px;
    width: 60px;
}
#elo{
    height: 30px;
    width: 50px;
}
#hipercard{
    height: 30px;
    width: 50px;
}
#amex{
    height: 30px;
    width: 50px;
}

.allBlack{
    background-color: black;
    height: 40px;
    position: absolute;
    width: 100%;
    left: 0%;
}

#labelBack{
    padding-top: 56px;
    padding-right: 4px;
    font-size: 8px;
}

#conteiner-cvv{
    display: flex;
    justify-content: end;
    align-items: center;
    background-color: white;
    width: 100%;
    height: 32px;
    border-radius: 4px;
    padding-right: 4px;
}

.logo-bandeira-back{
    display: flex;
    align-items: center;
    justify-content: center;
    padding-top: 12px;
}

#end-back{
    display: flex;
    flex-direction: column;
    align-items: end;
}

#container-name, #container-number{
    min-height: 40px;
}
</style>