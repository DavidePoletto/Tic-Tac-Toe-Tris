<template>
  <h1>TIC-TAC-TOE</h1>
  <div class="game">
    <PlayerInputPopup v-if="!playersSet" @names-submitted="setPlayerNames" />
    <div v-else class="game-content">
      <div class="player-info">
        <div class="p1">{{ players[0].name }}: {{ players[0].wins }}</div>
        <div class="p2">{{ players[1].name }}: {{ players[1].wins }}</div>
      </div>
      <TrisBoard :squares="squares" @square-click="handleClick" />
      <div class="turn-info">{{ turnMessage }}</div>
    </div>
    <ResultPopup v-if="gameOver" :message="resultMessage" @restart-game="restartGame" />
  </div>
</template>

<script>
import PlayerInputPopup from './PlayerInputPopup.vue';
import TrisBoard from './TrisBoard.vue';
import ResultPopup from './ResultPopup.vue';

export default {
  components: { PlayerInputPopup, TrisBoard, ResultPopup },
  data() {
    return {
      players: [
        { name: '', wins: 0 },
        { name: '', wins: 0 }
      ],
      currentPlayer: 0,
      squares: Array(9).fill(null),
      playersSet: false,
      gameOver: false,
      resultMessage: ''
    };
  },
  computed: {
    turnMessage() {
      return `Turno di ${this.players[this.currentPlayer].name}`;
    }
  },
  methods: {
    setPlayerNames({ player1, player2 }) {
      this.players[0].name = player1;
      this.players[1].name = player2;
      this.playersSet = true;
    },
    handleClick(index) {
      if (this.squares[index] || this.gameOver) {
        return;
      }
      // Aggiorna direttamente l'array reattivo
      this.squares.splice(index, 1, this.currentPlayer === 0 ? 'X' : 'O');
      if (this.calculateWinner()) {
        this.gameOver = true;
        this.players[this.currentPlayer].wins++;
        this.resultMessage = `${this.players[this.currentPlayer].name} ha vinto!`;
      } else if (!this.squares.includes(null)) {
        this.gameOver = true;
        this.resultMessage = `È un pareggio!`;
      } else {
        this.currentPlayer = 1 - this.currentPlayer;
      }
    },
    calculateWinner() {
      const lines = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6]
      ];
      for (let i = 0; i < lines.length; i++) {
        const [a, b, c] = lines[i];
        if (this.squares[a] && this.squares[a] === this.squares[b] && this.squares[a] === this.squares[c]) {
          return true;
        }
      }
      return false;
    },
    restartGame() {
      this.squares = Array(9).fill(null);
      this.currentPlayer = 0;
      this.gameOver = false;
      this.resultMessage = '';
    }
  }
};
</script>

<style scoped>

h1 {
  color: rgb(39, 172, 128);
  font-size: 50px;
  text-align: center;
}

.game {
  display: flex;
  flex-direction: column;
  align-items: center;
  
  margin-top: 150px;
}

.p1{
  color: rgb(250, 28, 28);
}
.player-info {
  display: flex;
  justify-content: space-around;
  width: 100%;
  margin-bottom: 20px;
  position: absolute;
  top: 100px;
  left: 0;
  font-size: 30px;
  color: rgb(255, 187, 0);
}
.turn-info {
  margin-top: 20px;
}
</style>
