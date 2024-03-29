<template>

    <div class="input-one">
        <label>{{ label }}</label>
        <input id="input-simple" :type="type" :placeholder="placeholder" @focus="focusEvent" @blur="blurEvent" :value="modelValue" @input="$emit('update:modelValue', $event.target.value)">
    </div>

</template>

<script>
export default {
    name: "Inputs",
    props: {
        label: {},
        type: {},
        placeholder: {},
        modelValue: {}
    },
    emits: ['update:modelValue'],
    methods:{
        focusEvent() {
            this.$emit('focus');
        }, 
        blurEvent() {
            this.$emit('blur');
        },
    },
}
</script>

<style scoped>

.input-one {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
    max-height: 52px;
}

.input-one input {
    border: solid 1px #cfcdcd;
    border-radius: 6px;
    width: auto;
}

#input-simple{
    height: 40px;
    padding: 8px;
}

.input-one label{
    font-family: Arial, Helvetica, sans-serif;
    font-size: 10px;
    font-weight: bold;
}

input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
}

input:focus {
    border-color: #479af8;
    outline: none;
}

</style>