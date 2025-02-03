<script setup lang="ts">
import ImgBlur from '/src/assets/img/Blur.png'
</script>

<template>
 <div class="card">
   <div class="card__image">
     <img :src="ImgBlur" alt=""/>
   </div>
   <div class="card__content">
     <div class="card__title">
       <h3>Заголовок</h3>
     </div>
     <div class="card__text">
       <span class="cls">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dignissimos, tempore!</span>
     </div>
   </div>
 </div>
</template>

<style scoped>
.card {
  width: 236px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  padding: 18px 14px;
  color: var(--color-typography-primary);
  border: 1px solid var(--color-background-thirdly);
  border-radius: var(--radius);
}
.card__content {
  display: flex;
  flex-direction: column;
  gap: 24px;
  align-items: center;
}

</style>