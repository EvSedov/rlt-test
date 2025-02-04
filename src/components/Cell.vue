<script setup lang="ts">
import DragElement from "./DragElement.vue";

const { element } = defineProps({element: {type: Object, default: null}});
</script>

<template>
  <div class="cell">
    <div class="cell__content">
      <DragElement v-if="element" :id="element.id" :srcIcon="element.icon" :name="element.name"  />
    </div>
    <div v-if="element && element.count" class="cell__count">{{ element.count }}</div>
  </div>
</template>

<style lang="scss" scoped>
.cell {
  width: 105px;
  height: 100px;
  display: flex;
  position: relative;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--color-background-thirdly);
}

.cell__count {
  position: absolute;
  bottom: 0;
  right: 0;
  padding: 2px 6px;
  color: var(--color-typography-primary);
  font-size: var(--font-size-small);
  border: 1px solid var(--color-background-thirdly);
  border-top-left-radius: 8px;
}
</style>