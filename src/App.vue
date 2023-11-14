<script setup>

</script>

<template>
  <h2>Rock Paper Scissors</h2>
  <input v-model="playerInput" placeholder="Your Choice...">
  <button @click="getPlayerInput">Play</button>
  <div>Player Choice: {{ playerChoiceDisp }}</div>
  <div>Computer Choice: {{ computerChoiceDisp }}</div>
  <div>Result: {{ result }}</div>
</template>

<script>
export default {
  data() {
    return {
      playerInput: '',
      playerChoiceDisp: '', 
      computerChoiceDisp: '', 
      result: ''
    }
  },
  methods: {
    getPlayerInput() {
      const input = this.playerInput.toLowerCase();
      if (input === "rock" || input === "paper" || input === "scissors") {
        this.displayGameResult(input);
      } else {
        alert("choice must be rock, paper, or scissors");
      }
    },
    getComputerChoice() {
      const randomNum = Math.floor(Math.random() * 3);
      switch (randomNum) {
        case 0:
          return "rock";
        case 1:
          return "paper";
        case 2:
          return "scissors";
      }
    },
    displayGameResult(userChoice) {
      const computerChoice = this.getComputerChoice();
      this.playerChoiceDisp = userChoice; 
      this.computerChoiceDisp = computerChoice; 
      const result = this.determineWinner(userChoice, computerChoice);
      this.result = result;
    },
    determineWinner(userChoice, computerChoice) {
      if (userChoice === computerChoice) {
        return "Tie";
      }
      if (userChoice === "rock") {
        return computerChoice === "paper" ? "PC won" : "Player won";
      }
      if (userChoice === "paper") {
        return computerChoice === "scissors" ? "PC won" : "Player won";
      }
      if (userChoice === "scissors") {
        return computerChoice === "rock" ? "PC won" : "Player won";
      }
      return "Invalid choice";
    }
  }
}
</script>

<style scoped>

</style>