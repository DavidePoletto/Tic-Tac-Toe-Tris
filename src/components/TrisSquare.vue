<template>
  <button class="square" @click="$emit('click')">
    {{ value }}
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
  width: 100px;
  height: 100px;
  font-size: 24px;
  border: 1px solid black;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>

