<script setup lang="ts">
import DragElement from "./DragElement.vue";

const { element } = defineProps({element: {type: Object, default: null}});
</script>

<template>
  <div class="cell">
    <div class="cell__content">
      <DragElement v-if="element" :id="element.id" :src="element.url" :name="element.name" />
    </div>
    <div v-if="element && element.count" class="cell__count">{{ element.count }}</div>
  </div>
</template>

<style scoped>
.cell {
  display: flex;
  position: relative;
  align-items: center;
  justify-content: center;
  width: 105px;
  height: 100px;
  border: 1px solid var(--color-background-thirdly)
}

.cell__count {

}
</style>