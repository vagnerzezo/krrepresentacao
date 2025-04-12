<script setup lang="ts">

import { ref, onMounted, onBeforeUnmount } from 'vue'

const isMobile = ref(false)
const isOpen = ref(false)

const checkIsMobile = () => {
  isMobile.value = window.matchMedia('(max-width: 767px)').matches
}

onMounted(() => {
  checkIsMobile()
  window.addEventListener('resize', checkIsMobile)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', checkIsMobile)
})

const navItems = [
  { label: 'HOME', to: '/' },
  { label: 'MARCAS', to: '/marcas' },
  { label: 'PRODUTOS', to: '/produtos' },
  { label: 'SHOWROOM', to: '/showroom' },
  { label: 'DEPOIMENTOS', to: '/depoimentos' },
]
</script>


<template>
  <header class="bg-white shadow-sm border-b border-gray-100">
    <div v-if="isMobile" class="relative flex flex-row justify-between p-2 w-full">
      <NuxtLink to="/" class="flex items-center space-x-2">
        <img src="/img/logo/logo.svg" alt="" class="w-auto h-6">
      </NuxtLink>

      <button @click="isOpen = !isOpen" data-collapse-toggle="navbar-default" type="button"
        class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200"
        aria-controls="navbar-default" aria-expanded="false">
        <span class="sr-only">Abrir menu</span>
        <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14">
          <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
            d="M1 1h15M1 7h15M1 13h15" />
        </svg>
      </button>

      <transition name="slide-left">
        <div v-if="isOpen" class="fixed top-0 left-0 w-full h-full bg-white shadow-md flex flex-col items-start justify-between space-y-2 px-6 py-10 z-50 rounded-none border-t border-gray-200">
          <button @click="isOpen = false" type="button"
            class="absolute top-4 right-4 inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200"
            aria-controls="navbar-default" aria-expanded="false">
            <span class="sr-only">Fechar menu</span>
            <svg class="w-4 h-6" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14">
              <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M1 13L16 1M1 1l15 12" />
            </svg>
          </button>
          <nav class="flex flex-col items-start space-y-6 pt-10">
            <NuxtLink @click="isOpen = false" v-for="item in navItems" :key="item.label" :to="item.to" class="text-gray-800 hover:text-black text-base font-medium tracking-wide transition"> {{ item.label }} </NuxtLink>
          </nav>
          <a href="https://wa.me/SEUNUMERO" target="_blank" class=" flex items-center justify-center bg-[#65B162] text-white w-full px-4 py-2 rounded-full shadow font-semibold hover:bg-green-600 transition">
            <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="23" height="23"
              viewBox="0 0 23 23" fill="none">
              <rect width="23" height="23" fill="url(#pattern0_8_6)" />
              <defs>
                <pattern id="pattern0_8_6" patternContentUnits="objectBoundingBox" width="1" height="1">
                  <use xlink:href="#image0_8_6" transform="scale(0.0434783)" />
                </pattern>
                <image id="image0_8_6" width="23" height="23" preserveAspectRatio="none"
                  xlink:href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABcAAAAXCAYAAADgKtSgAAAAAXNSR0IArs4c6QAAAKJlWElmTU0AKgAAAAgABgESAAMAAAABAAEAAAEaAAUAAAABAAAAVgEbAAUAAAABAAAAXgEoAAMAAAABAAIAAAExAAIAAAARAAAAZodpAAQAAAABAAAAeAAAAAAAAABgAAAAAQAAAGAAAAABd3d3Lmlua3NjYXBlLm9yZwAAAAOgAQADAAAAAQABAACgAgAEAAAAAQAAABegAwAEAAAAAQAAABcAAAAAZZ6rlwAAAAlwSFlzAAAOxAAADsQBlSsOGwAAActpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IlhNUCBDb3JlIDYuMC4wIj4KICAgPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4KICAgICAgPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIKICAgICAgICAgICAgeG1sbnM6dGlmZj0iaHR0cDovL25zLmFkb2JlLmNvbS90aWZmLzEuMC8iCiAgICAgICAgICAgIHhtbG5zOnhtcD0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wLyI+CiAgICAgICAgIDx0aWZmOk9yaWVudGF0aW9uPjE8L3RpZmY6T3JpZW50YXRpb24+CiAgICAgICAgIDx4bXA6Q3JlYXRvclRvb2w+d3d3Lmlua3NjYXBlLm9yZzwveG1wOkNyZWF0b3JUb29sPgogICAgICA8L3JkZjpEZXNjcmlwdGlvbj4KICAgPC9yZGY6UkRGPgo8L3g6eG1wbWV0YT4K56DsKAAAAppJREFUSA2VlUtIFVEYx52MHooEJtVFIrQ2QSkSGCRRuzKIgore4MIWkSQuolUItYjaRAStiiA3rlpEEiFUmAtbBAUFIpg9NMWeLgrFx/T7nzufnZnrXG9/+N3zPc/MnXPmTFCUojAMl5HaCwegHtZBGYzDIDyBB0EQDDAWJiYN4AS8B1+/ccZg1gvK7oANi85O0UroBFMXxjFYbc3YxVALl2AUpJ+wx2pyRpIroBekQdiZU5QIUFMK12AOZuBIoiTrktDfk/qgYsGilCD1x0GT69HVxcoI7AfpA6yJJQt06GvTBOg1LHFtMuAtSI02F/Zl0IK1WmyxkdoekE7a5DuyfthrzfhbQM9R+gjFlss3UrcLpOeuDkMLIrVYI/ZpF/n3s89y+UbKtY1HYBrK9Wxqo4anXuOIZ3/DfuP5qSYvVEjyGSyFGk2eAcmfsAd/yEWzb6Gfi8Kpw3CUyWjy0sj5Y+XcwQz2OdCdNPEXGyxXwDgV1SzX5N8jZ63fyAUe418BnTEP/QtgZ0DrolxSlVHgSxEFd0E6mKwipm1qeb0k12ETvARpGM74ffja51KVJtchJXX4RWYT1w7QntcOWEj9Xm11VPDOxXDK4BdMQpUVJkdyNdANtv8xna21ccK/oyBqt5ju3vb61flgikHtRjgLF2GrlWE3gB7dV1hlcU1uVzw6H/wPg349Dp31UlOslcAnmIXYuR0rSnHo2Q3jIN2KlRHY7MJhOMB4Cu6BLjYEzaBPW46IbwN9WGwNbmDHziDthPN03kx0z+HrHZAm4RXouzkNeh90ZKwHSW/kBd6LTuf5P0z+CKR+uA2HoBy2w334AUlp4V5AK5T48/m27vwwgT6ubGeCn9di6x9Ug+5UB9IofKZ+gjGv/gIMjfE+yvusigAAAABJRU5ErkJggg==" />
              </defs>
            </svg>
            <div class="flex flex-col gap-1 leading-tight ml-1">
              <span class="text-xs -mb-1">FALE COMIGO</span>
              <span class="text-md font-bold leading-none">WHATSAPP</span>
            </div>
          </a>
        </div>
      </transition>
    </div>

    <div v-else class="w-full mx-auto px-4">
      <div class="relative flex justify-center items-center py-6">
        <NuxtLink to="/" class="flex items-center space-x-2">
          <img src="/img/logo/logo.svg" alt="">
        </NuxtLink>

        <a href="https://wa.me/SEUNUMERO" target="_blank"
          class="absolute right-0 flex items-center bg-[#65B162] text-white px-4 py-2 rounded-full shadow font-semibold hover:bg-green-600 transition">
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="23" height="23"
            viewBox="0 0 23 23" fill="none">
            <rect width="23" height="23" fill="url(#pattern0_8_6)" />
            <defs>
              <pattern id="pattern0_8_6" patternContentUnits="objectBoundingBox" width="1" height="1">
                <use xlink:href="#image0_8_6" transform="scale(0.0434783)" />
              </pattern>
              <image id="image0_8_6" width="23" height="23" preserveAspectRatio="none"
                xlink:href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABcAAAAXCAYAAADgKtSgAAAAAXNSR0IArs4c6QAAAKJlWElmTU0AKgAAAAgABgESAAMAAAABAAEAAAEaAAUAAAABAAAAVgEbAAUAAAABAAAAXgEoAAMAAAABAAIAAAExAAIAAAARAAAAZodpAAQAAAABAAAAeAAAAAAAAABgAAAAAQAAAGAAAAABd3d3Lmlua3NjYXBlLm9yZwAAAAOgAQADAAAAAQABAACgAgAEAAAAAQAAABegAwAEAAAAAQAAABcAAAAAZZ6rlwAAAAlwSFlzAAAOxAAADsQBlSsOGwAAActpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IlhNUCBDb3JlIDYuMC4wIj4KICAgPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4KICAgICAgPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIKICAgICAgICAgICAgeG1sbnM6dGlmZj0iaHR0cDovL25zLmFkb2JlLmNvbS90aWZmLzEuMC8iCiAgICAgICAgICAgIHhtbG5zOnhtcD0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wLyI+CiAgICAgICAgIDx0aWZmOk9yaWVudGF0aW9uPjE8L3RpZmY6T3JpZW50YXRpb24+CiAgICAgICAgIDx4bXA6Q3JlYXRvclRvb2w+d3d3Lmlua3NjYXBlLm9yZzwveG1wOkNyZWF0b3JUb29sPgogICAgICA8L3JkZjpEZXNjcmlwdGlvbj4KICAgPC9yZGY6UkRGPgo8L3g6eG1wbWV0YT4K56DsKAAAAppJREFUSA2VlUtIFVEYx52MHooEJtVFIrQ2QSkSGCRRuzKIgore4MIWkSQuolUItYjaRAStiiA3rlpEEiFUmAtbBAUFIpg9NMWeLgrFx/T7nzufnZnrXG9/+N3zPc/MnXPmTFCUojAMl5HaCwegHtZBGYzDIDyBB0EQDDAWJiYN4AS8B1+/ccZg1gvK7oANi85O0UroBFMXxjFYbc3YxVALl2AUpJ+wx2pyRpIroBekQdiZU5QIUFMK12AOZuBIoiTrktDfk/qgYsGilCD1x0GT69HVxcoI7AfpA6yJJQt06GvTBOg1LHFtMuAtSI02F/Zl0IK1WmyxkdoekE7a5DuyfthrzfhbQM9R+gjFlss3UrcLpOeuDkMLIrVYI/ZpF/n3s89y+UbKtY1HYBrK9Wxqo4anXuOIZ3/DfuP5qSYvVEjyGSyFGk2eAcmfsAd/yEWzb6Gfi8Kpw3CUyWjy0sj5Y+XcwQz2OdCdNPEXGyxXwDgV1SzX5N8jZ63fyAUe418BnTEP/QtgZ0DrolxSlVHgSxEFd0E6mKwipm1qeb0k12ETvARpGM74ffja51KVJtchJXX4RWYT1w7QntcOWEj9Xm11VPDOxXDK4BdMQpUVJkdyNdANtv8xna21ccK/oyBqt5ju3vb61flgikHtRjgLF2GrlWE3gB7dV1hlcU1uVzw6H/wPg349Dp31UlOslcAnmIXYuR0rSnHo2Q3jIN2KlRHY7MJhOMB4Cu6BLjYEzaBPW46IbwN9WGwNbmDHziDthPN03kx0z+HrHZAm4RXouzkNeh90ZKwHSW/kBd6LTuf5P0z+CKR+uA2HoBy2w334AUlp4V5AK5T48/m27vwwgT6ubGeCn9di6x9Ug+5UB9IofKZ+gjGv/gIMjfE+yvusigAAAABJRU5ErkJggg==" />
            </defs>
          </svg>
          <div class="flex flex-col gap-1 leading-tight ml-1">
            <span class="text-[10px] -mb-1">FALE COMIGO</span>
            <span class="text-xs font-bold leading-none">WHATSAPP</span>
          </div>
        </a>
      </div>

      <nav class="flex justify-center space-x-6 pb-4">
        <NuxtLink v-for="item in navItems" :key="item.label" :to="item.to"
          class="text-gray-800 hover:text-black text-sm font-medium tracking-wide transition">
          {{ item.label }}
        </NuxtLink>
      </nav>
    </div>


  </header>
</template>

<style scoped>
/* Transição suave da direita para a esquerda */
.slide-left-enter-active,
.slide-left-leave-active {
  transition: transform 0.3s ease, opacity 0.3s ease;
}

.slide-left-enter-from {
  transform: translateX(100%);
  opacity: 0;
}

.slide-left-enter-to {
  transform: translateX(0);
  opacity: 1;
}

.slide-left-leave-from {
  transform: translateX(0);
  opacity: 1;
}

.slide-left-leave-to {
  transform: translateX(100%);
  opacity: 0;
}
</style>