<template>
  <div class="result-popup">
    <div class="result-message">{{ message }}</div>
    <button @click="$emit('restart-game')">Restart</button>
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
.result-popup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 20px;
  border: 1px solid black;
  text-align: center;
}
</style>
