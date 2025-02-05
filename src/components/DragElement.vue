<script setup lang="ts">
const { srcIcon } = defineProps({
  id: { type: Number, required: true },
  name: { type: String, default: "" },
  srcIcon: { type: String, default: "" },
  count: { type: Number, default: null },
});
</script>

<template>
  <div class="element" :id="`${id}`">
    <img :src="srcIcon" :alt="name" />
    <div v-if="count" class="element__count">{{ count }}</div>
  </div>
</template>

<style lang="scss" scoped>
.element {
  width: 100%;
  height: 100%;
  cursor: pointer;

  .element__count {
    position: absolute;
    bottom: 0;
    right: 0;
    padding: 2px 6px;
    color: var(--color-typography-primary);
    font-size: var(--font-size-small);
    border: 1px solid var(--color-background-thirdly);
    border-top-left-radius: 8px;
  }
}
</style>
