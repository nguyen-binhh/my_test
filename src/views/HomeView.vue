<script setup lang="ts">
import { ref } from 'vue'
import { getPhotoCards } from '@/services/images'
import type { TypePhotoCard } from '@/utils/type'

import Header from '@/components/HeaderCpn.vue'
import Card from '@/components/CardCpn.vue'

const cards = ref<TypePhotoCard[]>([])
async function fetchCards() {
  try {
    const data = await getPhotoCards()
    cards.value = data
  } catch (error) {
    console.error('Failed to fetch photo cards:', error)
  }
}
fetchCards()
</script>

<template>
  <div id="app">
    <Header />
    <div class="content">
      <h2 class="heading">Photo Cards</h2>
      <div class="content__wrapper">
        <Card
          v-for="({ image, text }, index) in cards"
          :key="index"
          :imageSrc="image"
          :text="text"
        />
      </div>
    </div>
  </div>
</template>
