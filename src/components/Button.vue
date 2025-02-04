<script setup lang="ts">
const { text, textColor, bgColor } = defineProps({
  text: {type: String, default: 'Нажать'},
  textColor: { type: String, default: '#000000' },
  bgColor: { type: String, default: '#FFFFFF' },
});
const emits = defineEmits(["onClick"]);
</script>

<template>
 <button type="button" class="button" @click="emits('onClick')">{{ text }}</button>
</template>

<style lang="scss" scoped>
.button {
  width: 100%;
  padding: 11px 15px;
  font-size: 14px;
  text-align: center;
  text-wrap: nowrap;
  color: v-bind(textColor);
  background-color: v-bind(bgColor);
}
</style>