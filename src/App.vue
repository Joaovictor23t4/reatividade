<template>
  <div class="container-pai">
    <Exercicio />
  </div>
</template>

<script setup>
import Exercicio from './components/Exercicio.vue';
</script>

<style scoped>
.container-pai {
  height: 90vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
}
</style>
