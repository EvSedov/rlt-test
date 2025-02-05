<script setup lang="ts">
import Button from "./Button.vue";
const countToDelete = defineModel<number>("countToDelete", { default: 0 });
const emits = defineEmits(["cancellation", "confirmation"]);
</script>

<template>
  <div class="items-to-delete">
    <input
      type="number"
      class="input"
      placeholder="Введите количество"
      v-model="countToDelete"
    />
    <div class="items-to-delete__buttons">
      <Button text="Отмена" @click="emits('cancellation')" />
      <Button
        text="Подтвердить"
        bg-color="#FA7272"
        text-color="#FFFFFF"
        @click="emits('confirmation')"
      />
    </div>
  </div>
</template>

<style scoped lang="scss">
.items-to-delete {
  width: 250px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  padding: 25px 15px 18px;
  color: var(--color-typography-primary);
  background-color: var(--color-background-secondary);
  border: 1px solid var(--color-background-thirdly);

  .input {
    padding: 11px 12px 12px;
    font-size: 14px;
    color: var(--color-typography-primary);
    background: transparent;
    border: 1px solid var(--color-background-thirdly);
    border-radius: 4px;
  }

  .items-to-delete__buttons {
    display: flex;
    gap: 10px;
  }
}
</style>
