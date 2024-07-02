<template>
  <div id="app">
    <div class="image-container">
      <img src="@/assets/IMG/background.jpg" alt="background">
    </div>
      <TrisGame />
  </div>
</template>

<script>
import TrisGame from './components/TrisGame.vue';

export default {
  name: 'App',
  components: {
    TrisGame
  }
};
</script>

<style scoped>
.image-container {
  z-index: -1;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;

}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}


</style>
