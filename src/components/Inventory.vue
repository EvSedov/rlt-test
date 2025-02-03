<script setup lang="ts">

import Card from "./Card.vue";
import Board from "./Board.vue";
</script>

<template>
 <div class="inventory">
   <Card />
   <Board />
 </div>
</template>

<style scoped>
.inventory {
  display: flex;
  gap: 24px;
  margin-bottom: 24px;
}
</style>