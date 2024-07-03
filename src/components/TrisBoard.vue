<template>
  <div class="board">
    <TrisSquare
      v-for="(square, index) in squares"
      :key="index"
      :value="square"
      @click="handleClick(index)"
      :class="{
        'top-border': index >= 3,
        'left-border': index % 3 !== 0
      }"
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
  gap: 0;
  background-color: transparent;
}

.top-border {
  border-top: 5px solid black;
}

.left-border {
  border-left: 5px solid black;
}
</style>

