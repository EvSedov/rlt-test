<script setup lang="ts">

import Cell from "./Cell.vue";
import {ref} from "vue";
const cells = ref([1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25]);
</script>

<template>
  <div class="board">
    <Cell v-for="item in cells" :key="item" />
  </div>
</template>

<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  border: 1px solid var(--color-background-thirdly);
  border-radius: var(--radius);
  overflow: hidden;
}
</style>