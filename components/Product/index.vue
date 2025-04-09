<template>
 <div class="max-w-7xl mx-auto py-10 px-4">
  <!-- Título -->
  <h2 class="text-center text-2xl font-bold mb-6">PRODUTOS</h2>

  <!-- Abas -->
  <div class="flex justify-center gap-3 mb-8 flex-wrap">
   <button v-for="brand in brands" :key="brand" @click="activeBrand = brand"
    :class="['px-6 py-2 rounded-full text-sm font-semibold transition', activeBrand === brand ? 'bg-black text-white' : 'bg-gray-100 text-gray-800 hover:bg-gray-200']">
    {{ brand }}
   </button>
  </div>

  <!-- Produtos -->
  <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
   <div v-for="product in filteredProducts" :key="product.id" class="bg-white rounded-lg p-4 text-center">
    <img :src="product.image" alt="Produto" class="w-full h-auto object-contain" />
   </div>
  </div>
 </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

// Abas/marcas
const brands = ['QIX SKATEBOARD', 'WESTCOAST', 'ORANGE', 'FIVEBUCKS']
const activeBrand = ref(brands[0])

// Produtos mockados
const products = [
 {
  id: 1,
  brand: 'QIX SKATEBOARD',
  image: '/img/produtos/produto-1.png'
 },
 {
  id: 2,
  brand: 'QIX SKATEBOARD',
  image: '/img/produtos/produto-2.png'
 },
 {
  id: 3,
  brand: 'WESTCOAST',
  image: '/img/produtos/produto-3.png'
 },
 {
  id: 4,
  brand: 'ORANGE',
  image: '/img/produtos/produto-4.png'
 },
 {
  id: 5,
  brand: 'FIVEBUCKS',
  image: '/img/produtos/produto-1.png'
 }
]

// Filtra por aba ativa
const filteredProducts = computed(() =>
 products.filter((p) => p.brand === activeBrand.value)
)
</script>