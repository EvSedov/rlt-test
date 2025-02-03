<script setup lang="ts">
import ItemFirst from '/src/assets/img/ItemFirst.png';
import ItemSecond from '/src/assets/img/ItemSecond.png';
import ItemThird from '/src/assets/img/ItemThird.png';
import Cell from "./Cell.vue";
import {ref} from "vue";
const elements = ref([
  { id: 1, name: "Element 1", url: ItemFirst, count: 4 },
  { id: 2, name: "Element 2", url: ItemSecond, count: 2 },
  { id: 3, name: "Element 3", url: ItemThird, count: 5 },
  null, null, null, null, null, null, null, null, null, null, null,
  null, null, null, null, null, null, null, null, null, null, null
]);
</script>

<template>
  <div class="board">
    <div v-for="(item, index) in elements" :key="index">
      <Cell v-if="item && item.id" :element="item" />
      <Cell v-else />
    </div>
  </div>
</template>

<style scoped>
.board {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(5, 100px);
  border: 1px solid var(--color-background-thirdly);
  border-radius: var(--radius);
  overflow: hidden;
}
</style>