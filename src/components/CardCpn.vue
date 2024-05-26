<script setup>
const { imageSrc, text } = defineProps({
  imageSrc: {
    type: String,
    required: true
  },
  text: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="card">
    <img :src="imageSrc" alt="Image" class="card-image" />
    <div class="card-content">
      <p class="card-text">{{ text }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import '../assets/card.scss';
</style>
