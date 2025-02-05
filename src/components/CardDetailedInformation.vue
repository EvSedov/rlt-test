<script setup lang="ts">
import Button from "./Button.vue";
const { element } = defineProps({element: {type: Object, default: null}});
const emits = defineEmits(['deleting'])
</script>

<template>
<div class="card-detailed-information">
  <div class="card-detailed-information__image">
    <img :src="element.icon" :alt="element.name" />
  </div>
  <div class="card-detailed-information__content">
    <div class="card-detailed-information__title">
      {{ element.name }}
    </div>
    <div class="card-detailed-information__description">
      {{ element.description }}
    </div>
  </div>
  <div class="card-detailed-information__footer">
    <Button bg-color="#FA7272" text-color="#FFFFFF" text="Удалить предмет" @click="emits('deleting')" />
  </div>
</div>
</template>

<style lang="scss" scoped>
.card-detailed-information {
  width: 250px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 25px 15px 18px;
  color: var(--color-typography-primary);
  background-color: var(--color-background-secondary);
  opacity: 0.7;
  border: 1px solid var(--color-background-thirdly);

  .card-detailed-information__image {
    padding: 30px 40px;
    border-bottom: 2px solid var(--color-background-thirdly);

    img {
      width: 130px;
      height: 130px;
    }
  }

  .card-detailed-information__content {
    padding-top: 16px;
    padding-bottom: 20px;
    border-bottom: 2px solid var(--color-background-thirdly);

    .card-detailed-information__title {
      margin-bottom: 20px;
      font-weight: bold;
    }

  }

  .card-detailed-information__footer {
    padding: 18px 0;
    width: 100%;
  }
}


</style>