<script setup lang="ts">
const { countElement } = defineProps({
  cellId: {type: Number, default: null},
  countElement: { type: Number, default: null }
});

const emits = defineEmits(["dropCell"]);

const onDrop = (event: DragEvent) => {
  const elementId = parseInt(event.dataTransfer!.getData('elementId'));
  emits('dropCell', elementId);
}
</script>

<template>
  <div
      class="cell"
      @drop="onDrop($event)"
      @dragover.prevent
      @dragenter.prevent
  >
    <div class="cell__content">
      <slot/>
    </div>
    <div v-if="countElement" class="cell__count">{{ countElement }}</div>
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