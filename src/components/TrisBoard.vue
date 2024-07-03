<template>
  <div class="board">
    <TrisSquare
      v-for="(square, index) in squares"
      :key="index"
      :value="square"
      @click="handleClick(index)"
    />
  </div>
</template>

<script>
import TrisSquare from './TrisSquare.vue';

export default {
  components: { TrisSquare },
  props: {
    squares: Array
  },
  methods: {
    handleClick(index) {
      this.$emit('square-click', index);
    }
  }
};
</script>

<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  gap: 5px;
  background-color: rgb(0, 0, 0);
}
</style>
