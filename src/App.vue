<template>
  <div id="app">
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

<style>
#app {
  height: 100vh;
  

}
</style>
