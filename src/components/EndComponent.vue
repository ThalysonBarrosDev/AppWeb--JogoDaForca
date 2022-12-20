<template>
    <div class="end">
        <div :class="`end-text ${stage}`">
            {{ text }}
        </div>

        <button class="end-button" v-on:click="playAgain()">Jogar Novamente</button>
    </div>
</template>

<script>
export default {
    name: 'EndComponent',
    props: {
        stage: String,
        text: String,
        playAgain: Function
    }
}
</script>

<style>
.end-text {
    margin: 50px 0;
    font-size: 24px;
    font-weight: 600;
}

.hanged {
    color: var(--color-text-error);
}

.winner {
    color: var(--color-text-success);
}
</style>