<template>
  <button class="square" @click="$emit('click')">
    <span :class="{'x-player': value === 'X', 'o-player': value === 'O'}">{{ value }}</span>
  </button>
</template>

<script>
export default {
  props: {
    value: String
  }
};
</script>

<style scoped>
.square {
  z-index: 1;
  width: 100px;
  height: 100px;
  font-size: 24px;
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #fcfcfc; 
}
.x-player {
  color: rgb(234, 16, 16);
  font-size: 50px;
  font-weight: 600;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
.o-player {
  color: rgb(255, 199, 32);
  font-size: 50px;
  font-weight: 600;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>


