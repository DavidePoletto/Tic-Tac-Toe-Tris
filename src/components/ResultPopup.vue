<template>
  <div class="overlay1">
    <div class="result-popup">
      <div class="result-message">{{ message }}</div>
      <button class="restart-button" @click="$emit('restart-game')">Reset</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    message: String
  }
};
</script>

<style scoped>

.overlay1{
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1;
}

.result-popup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 20px;
  text-align: center;
  z-index: 1;
  width: 200px;
  height: 100px;
  font-size: 25px;
  border-radius: 8px;
}

.restart-button{
  color: rgb(28, 175, 209);
  margin-top: 20px;
  border-radius: 7px;
  padding: 5px;
  border: none;
  background-color: rgb(230, 236, 241);
}

.result-message{
  margin-top: 20px;
  font-weight: 600;
}

</style>
