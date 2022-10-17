<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue';
import Rules from './components/Rules.vue';
import Game from './components/Game.vue';
import Results from './components/Results.vue';

const score = ref(0)
const gameType = ref("play")
const playerSelect = ref("")

const setPlayer = (select) => {
  playerSelect.value = select
  gameType.value = "result"
}

const setScore = (result) => {
  if (result === 'YOU WIN')
    score.value = score.value + 1
}

const changeGameType = () => {
  gameType.value = "play"
}

</script>

<template>
  <div class="container mx-auto p-8">
    <Header :score="score" />
    <Game v-if="gameType === 'play'" @set-player-select="setPlayer" />
    <Results v-else :player="playerSelect" @play-again="changeGameType" @set-score="setScore" />
    <Rules />
  </div>
</template>