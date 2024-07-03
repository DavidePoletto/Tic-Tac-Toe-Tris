<template>
  <div class="overlay">
    <div class="popup">
      <h2>Inserisci i nomi dei giocatori</h2>
      <div class="input-group1">
        <label for="player1">Giocatore 1:</label>
        <input id="player1" v-model="player1" />
      </div>
      <div class="input-group2">
        <label for="player2">Giocatore 2:</label>
        <input id="player2" v-model="player2" />
      </div>
      <button class="start-button" @click="submitNames">Inizia Partita</button>
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

.input-group1 {
  margin-bottom: 10px;
  color: rgb(250, 28, 28);
  font-weight: 600;
}

.input-group2 {
  margin-bottom: 20px;
  color: rgb(255, 187, 0);
  font-weight: 600;
}

.input-group1 input{
  border: none;
  border-bottom: 2px solid rgb(255, 31, 31);
  width: 30%;
}

.input-group2 input{
  border: none;
  border-bottom: 2px solid rgb(255, 187, 0);
  width: 30%;
}

.popup h2{
  color: rgb(28, 175, 209);
}

.start-button{
  color: rgb(28, 175, 209);
  border-radius: 7px;
  padding: 5px;
  border: none;
  background-color: rgb(230, 236, 241);
}

</style>

