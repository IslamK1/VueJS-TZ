<template>
  <div class="container py-4">
    <Filters :filters="filters" @update="updateFilters" />

    <div class="row g-3">
      <div
        v-for="apartment in filteredApartments"
        :key="apartment.id"
        class="col-md-4 col-sm-6"
      >
        <ApartmentCard :apartment="apartment" />
      </div>
    </div>

    <div v-if="filteredApartments.length === 0" class="text-center mt-4">
      <p>По вашему запросу ничего не найдено</p>
    </div>
  </div>
</template>

<script setup>


import { ref, computed } from 'vue'
import apartmentsData from './data/apartments.json'
import Filters from './components/Filters.vue'
import ApartmentCard from './components/ApartmentCard.vue'

const apartments = ref(apartmentsData)

const filters = ref({
  areaFrom: null,
  areaTo: null,
  roomsFrom: null,
  roomsTo: null,
  address: ''
})

const updateFilters = (newFilters) => {
  filters.value = newFilters
}

const filteredApartments = computed(() => {
  return apartments.value.filter(a => {
    if (filters.value.areaFrom && a.area < filters.value.areaFrom) return false
    if (filters.value.areaTo && a.area > filters.value.areaTo) return false
    if (filters.value.roomsFrom && a.rooms < filters.value.roomsFrom) return false
    if (filters.value.roomsTo && a.rooms > filters.value.roomsTo) return false
    if (
      filters.value.address &&
      !a.address.toLowerCase().includes(filters.value.address.toLowerCase())
    ) return false

    return true
  })
})
</script>
