<template>
  <div id="app">
    <h1>Jogo da Forca</h1>

    <section id="init" v-if="display === 'init'">
      <FormComponent v-if="stage === 'word'"
        titleForm="Defina sua Palavra"
        buttonForm="Próximo"
        :action="setWord"
      />

      <FormComponent v-if="stage === 'tip'"
        titleForm="Defina a Dica"
        buttonForm="Iniciar o Jogo"
        :action="setTip"
      />
    </section>

    <section id="game" v-if="display === 'game'">
      <GameComponent 
        :errors="errors"
        :word="word"
        :tip="tip"
        :checkLetter="checkLetter"
        :stage="stage"
        :letters="letters"
        :toPlay="toPlay"
        :playAgain="playAgain"
      />
    </section>
  </div>
</template>

<script>
import './assets/css/global.css';
import FormComponent from './components/FormComponent';
import GameComponent from './components/GameComponent';

export default {
  name: 'App',
  data() {
    return {
      display: 'init',
      stage: 'word',
      word: '',
      tip: '',
      errors: 0,
      letters: []
    }
  },
  components: {
    FormComponent,
    GameComponent
  },
  methods: {
    setWord: function(word) {
      this.word = word;
      this.stage = 'tip';
    },
    setTip: function(tip) {
      this.tip = tip;
      this.display = 'game';
      this.stage = 'game';
    },
    checkLetter: function(letter) {
      return this.letters.find(i => i.toLowerCase() === letter.toLowerCase());
    },
    toPlay: function(letter) {
      this.letters.push(letter);

      this.checkErrors(letter);
    },
    checkErrors: function(letter) {
      if(this.word.toLowerCase().indexOf(letter.toLowerCase()) >= 0) {
        return this.checkSuccess();
      }

      this.errors++;

      if (this.errors === 6) {
        this.stage = 'hanged';
      }
    },
    checkSuccess: function() {
      let lettersOnly = [...new Set(this.word.split(''))];

      if(lettersOnly.length === (this.letters.length - this.errors)) {
        this.stage = 'winner';
      }
    },
    playAgain: function() {
      this.display = 'init';
      this.word = '';
      this.tip = '';
      this.errors = 0;
      this.letters = [];
      this.stage = 'word'
    }
  }
}
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
