<script setup lang="ts">
import {ref} from "vue";

const hide = ref<boolean>(false);
const close = (): void => { hide.value = true };
</script>

<template>
<div v-if="!hide" class="footer">
  <div class="footer__content">
    <p>Текст в подвале</p>
  </div>
  <button type="button" class="close" aria-label="Close" @click="close">
    <span aria-hidden="true">&#10006;</span>
  </button>
</div>
</template>

<style lang="scss" scoped>
 .footer {
   position: relative;
   display: flex;
   justify-content: space-between;
   width: 785px;
   color: var(--color-typography-primary);
   border: 1px solid var(--color-background-thirdly);
   border-radius: var(--radius);
   padding: 18px;
   background-color: var(--color-background-secondary);
 }

 .footer__content {
   width: 90%;
   padding: 6px;
   border-radius: var(--radius);
   background: var(--gradient);
 }

 .close {
   position: absolute;
   top: 8px;
   right: 8px;
   height: 24px;
   width: 24px;
   margin-left: 0;
   padding: 0;
   color: var(--color-typography-primary);
   background-color: Transparent;
   background-repeat:no-repeat;
   cursor:pointer;
   overflow: hidden;
   outline:none;
 }
</style>