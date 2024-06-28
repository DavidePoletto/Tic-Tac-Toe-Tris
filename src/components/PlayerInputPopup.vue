<template>
  <div class="overlay">
    <div class="popup">
      <h2>Inserisci i nomi dei giocatori</h2>
      <div class="input-group">
        <label for="player1">Giocatore 1:</label>
        <input id="player1" v-model="player1" />
      </div>
      <div class="input-group">
        <label for="player2">Giocatore 2:</label>
        <input id="player2" v-model="player2" />
      </div>
      <button @click="submitNames">Inizia Partita</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      player1: '',
      player2: ''
    };
  },
  methods: {
    submitNames() {
      this.$emit('names-submitted', { player1: this.player1, player2: this.player2 });
    }
  }
};
</script>

<style scoped>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
}

.popup {
  background: white;
  padding: 20px;
  border-radius: 8px;
  text-align: center;
}

.input-group {
  margin-bottom: 10px;
}
</style>

