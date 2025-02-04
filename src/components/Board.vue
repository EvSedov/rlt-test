<script setup lang="ts">
import ItemFirst from '/src/assets/img/ItemFirst.png';
import ItemSecond from '/src/assets/img/ItemSecond.png';
import ItemThird from '/src/assets/img/ItemThird.png';
import Cell from "./Cell.vue";
import {ref} from "vue";

const selectedIndex = ref<number | null>(null);
const selectedItem = ref<{ id: number, name: string, icon: string, count: number } | null>(null)
const elements = ref([
  { id: 0, name: "Element 1", icon: ItemFirst, count: 4 },
  { id: 1, name: "Element 2", icon: ItemSecond, count: 2 },
  { id: 2, name: "Element 3", icon: ItemThird, count: 5 },
  null, null, null, null, null, null, null, null, null, null, null,
  null, null, null, null, null, null, null, null, null, null, null
]);

const selectItem = (item: { id: number, name: string, icon: string, count: number }, index: number) => {
  selectedItem.value = item;
  selectedIndex.value = index;
  console.log({item: selectedItem.value, index: index});
}
</script>

<template>
  <div class="board">
    <div v-for="(item, index) in elements" :key="`${index}-${item?.name}`">
      <Cell v-if="item" :element="item" @click="selectItem(item, index)"/>
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