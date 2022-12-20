<template>
    <div class="game">
        <GallowsComponent 
            :errors="errors" 
        />

        <WordComponent 
            :word="word"
            :tip="tip"
            :checkLetter="checkLetter"
            :stage="stage"
        />

        <KeyboardComponent 
            v-if="stage === 'game'"
            :letters="letters"
            :checkLetter="checkLetter"
            :toPlay="toPlay"
        /> 

        <EndComponent 
            v-if="stage !== 'game'"
            :stage="stage"
            :text="stage === 'winner' ? 'Parabéns :)' : 'Putz :('"
            :playAgain="playAgain" 
        />
    </div>
</template>

<script>
import GallowsComponent from './GallowsComponent';
import WordComponent from './WordComponent';
import KeyboardComponent from './KeyboardComponent';
import EndComponent from './EndComponent';

export default {
    name: 'GameComponent',
    props: {
        errors: Number,
        word: String,
        tip: String,
        checkLetter: Function,
        stage: String,
        letters: Array,
        toPlay: Function,
        playAgain: Function
    },
    components: {
        GallowsComponent,
        WordComponent,
        KeyboardComponent,
        EndComponent
    }
}
</script>

<style>
.game {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
}
</style>