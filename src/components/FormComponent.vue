<template>
    <div class="form">
        <div class="form-title">{{ titleForm }}</div>

        <input type="text" class="form-input" v-model="inputValue">

        <button :disable="inputValue.length === 0" v-on:click="onSubmit">{{ buttonForm }}</button>
    </div>
</template>

<script>
export default {
    name: 'FormComponent',
    props: {
        titleForm: String,
        buttonForm: String,
        action: Function
    },
    data() {
        return {
            inputValue: ''
        }
    },
    methods: {
        onSubmit: function() {
            this.action(this.inputValue);
            this.inputValue = '';
        }
    }
}
</script>

<style>
.form {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    justify-content: center;
    margin-top: 20px;
}

.form-input {
    padding: 10px 5px;
    border: 0;
    border-radius: 5px;
    margin: 10px 0;
    text-align: center;
    color: var(--color-text-dark);
    font-size: 16px;
}
</style>