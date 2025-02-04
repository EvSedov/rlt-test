<script setup lang="ts">
const { srcIcon } = defineProps({
  id: { type: Number, required: true },
  name: { type: String, default: '' },
  srcIcon: { type: String, default: ''},
});
</script>

<template>
  <div class="element" :id="`${id}`">
    <img :src="srcIcon" :alt="name"/>
  </div>
</template>

<style lang="scss" scoped>
.element {
  cursor: pointer;
}
</style>