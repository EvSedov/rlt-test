<script setup lang="ts">
const emits = defineEmits(["dropCell"]);

const onDrop = (event: DragEvent) => {
  const elementId = parseInt(event.dataTransfer!.getData("elementId"));
  emits("dropCell", elementId);
};
</script>

<template>
  <div class="cell" @drop="onDrop($event)" @dragover.prevent @dragenter.prevent>
    <div class="cell__content">
      <slot />
    </div>
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
</style>
