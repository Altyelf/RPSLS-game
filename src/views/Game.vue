<template>
  <div class="game-container">
    <div class="image-wrapper">
      <img
      src="../assets/images/sheldon-image.png"
      alt="Sheldon image"
      class="sheldon-image">
      <img
      alt="Game logo"
      src="../assets/images/rpsls-image.jpg"
      class="main-image">
      <img
      alt="User image"
      src="../assets/images/user-image.png"
      class="user-image">
    </div>
    <h4 class="score-text">Score</h4>
    <div class="score-box">
      <div class="inner-border">
        <div class="score-box--container">
          <h4>
            Sheldon
            <span class="score-box--count score-box--computer">
              {{ computerWins }}
            </span>
          </h4>
        </div>
        <div class="score-box--container">
          <h4>
            User
            <span class="score-box--count score-box--user">
              {{ userWins }}
            </span>
          </h4>
        </div>
      </div>
    </div>
     <div class="game-board">
      <h1 class="computer-guess">
        {{ computerGuess ? computerGuess : 'Make a Move' }}
      </h1>
      <ul class="emojis">
        <li
          class="emoji"
          v-for="emoji in emojis" v-bind:key="emoji.name"
          @click="chooseEmoji(emoji.symbol)">
          {{ emoji.symbol }}
          <span class="name">
            {{ emoji.name}}
          </span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang='ts'>
import { defineComponent } from 'vue';

export default defineComponent({

  data() {
    return {
      emojis: [
        {
          name: 'Rock',
          symbol: '👊',
        },
        {
          name: 'Paper',
          symbol: '✋',
        },
        {
          name: 'Scissor',
          symbol: '✌️',
        },
        {
          name: 'Lizard',
          symbol: '🦎',
        },
        {
          name: 'Spock',
          symbol: '🖖',
        },
      ],
      computerGuess: '',
      computerWins: 0,
      userWins: 0,
    };
  },
  methods: {
    chooseEmoji(selection: string) {
      const computerGuess = this.emojis[Math.floor(Math.random() * this.emojis.length)];
      this.computerGuess = computerGuess.symbol;
      if (
        (selection === '👊' && this.computerGuess === '✌️')
          || (selection === '✌️' && this.computerGuess === '✋')
          || (selection === '✋' && this.computerGuess === '👊')
          || (selection === '👊' && this.computerGuess === '🦎')
          || (selection === '🦎' && this.computerGuess === '🖖')
          || (selection === '✌️' && this.computerGuess === '🦎')
          || (selection === '🦎' && this.computerGuess === '✋')
          || (selection === '✋' && this.computerGuess === '🖖')
          || (selection === '🖖' && this.computerGuess === '👊')
      ) {
        this.userWins += 1;
      } else if (selection === computerGuess.symbol) {
        return "It's a tie!";
      } else {
        this.computerWins += 1;
      }
      return computerGuess;
    },
  },
});
</script>

<style lang="scss">
  @import './Game.scss';
</style>
