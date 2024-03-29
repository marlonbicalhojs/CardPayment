<template>

    <div class="dateContainer">
        <div class="mes-container">
            <label for="mes">Data de expiração</label>
            <select id="mes" @change="emitirValoresMes">
                <option value="">Mês</option>
                <option value="01">01</option>
                <option value="02">02</option>
                <option value="03">03</option>
                <option value="04">04</option>
                <option value="05">05</option>
                <option value="06">06</option>
                <option value="07">07</option>
                <option value="08">08</option>
                <option value="09">09</option>
                <option value="10">10</option>
                <option value="11">11</option>
                <option value="12">12</option>
            </select>
        </div>
        <div class="ano-container">
            <select id="ano" @change="emitirValoresAno">
                <option value="">Ano</option>
                <option value="24">2024</option>
                <option value="25">2025</option>
                <option value="26">2026</option>
                <option value="27">2027</option>
                <option value="28">2028</option>
                <option value="29">2029</option>
                <option value="30">2030</option>
                <option value="31">2031</option>
                <option value="32">2032</option>
            </select>
        </div>

    </div>

</template>

<script>
export default {
  name: 'DateInput',
  methods: {
    emitirValoresMes(event) {
      const mesSelecionado = event.target.value;
      this.$emit('valoresSelecionados', {mes: mesSelecionado });
    },
    emitirValoresAno(event) {
      const anoSelecionado = this.$el.querySelector('#ano').value;
      this.$emit('valoresSelecionados', {ano: anoSelecionado });
    }
    }
}
</script>

<style>

.dateContainer {
    display: flex;
    justify-content: center;
    align-items: center;
    align-items: end;
    margin-right: 28px;
}

select{
    display: flex;
    border: solid 1px #cfcdcd;
    border-radius: 6px;
    height: 40px;
    width: 120px;
}

select:focus{
    border-color: #479af8;
    outline: none;
}

label{
    font-family: Arial, Helvetica, sans-serif;
    font-size: 10px;
    font-weight: bold;
}

.mes-container{
    display: flex;
    flex-direction: column;
    margin-right: 12px;
}

#mes, #ano{
    display: flex;
    padding: 8px;
    font-size: 16px;

}

</style>