<template>
  <div class="container">
    <div>
      <h1 class="welcome">
        yI'el!
      </h1>
      <p class="title">
      Rock, Paper, Scissors, Lizard, Spock
      </p>
    </div>
      <router-link :to="'/game/'" >
        <button class="play-button">
         Play
        </button>
      </router-link>
  </div>
</template>

<script lang="ts">
import { Vue } from 'vue-class-component';

export default class Home extends Vue {}
</script>
