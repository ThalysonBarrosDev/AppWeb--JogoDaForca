<template>
    <div class="keyboard">
        <button 
            class="keyboard-button" v-for="(letter, key) in 'abcdefghijklmnopqrstuvwxyz'" 
            :key="key" 
            :disabled="checkLetter(letter)"
            v-on:click="toPlay(letter)"
        >
            {{ letter }}
        </button>
    </div>
</template>

<script>
export default {
    name: 'KeyboardComponent',
    props: {
        letters: Array,
        checkLetter: Function,
        toPlay: Function
    }
}
</script>

<style>
.keyboard {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    max-width: 85%;
    margin-top: 35px;
}

.keyboard-button {
    margin: 5px;
    text-transform: uppercase;
}
</style>