<script setup lang="ts">
const { src } = defineProps({
  id: { type: String, required: true },
  name: { type: String, default: '' },
  src: { type: String, default: ''},
});
</script>

<template>
  <div class="element" :id>
    <img :src="src" :alt="name"/>
  </div>
</template>

<style scoped>

</style>