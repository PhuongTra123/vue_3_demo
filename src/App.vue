<script setup>
import { ref } from 'vue'
import SearchInput from './components/SearchInput.vue'
import WeatherCard from './components/WeatherCard.vue'

const places = ref(null)

const addPlace = (data) => {
  places.value = data
}

const deletePlace = (name) => {
  places.value = null

}
</script>
<template>
  <main class="mx-auto container mt-[60px]">
    <!-- Date -->
    <div class="text-center mb-6 text-[20px] font-bold">
      {{
        new Date().toLocaleDateString('en-us', {
          weekday: 'long',
          year: 'numeric',
          month: 'long',
          day: 'numeric'
        })
      }}
    </div>

    <!-- Search -->
    <div>
      <SearchInput @place-data="addPlace" />
    </div>

    <!-- Weather cards -->
    <div v-if="places" class="m-auto">
        <WeatherCard :place="places" @delete-place="deletePlace" />
    </div>
  </main>
</template>