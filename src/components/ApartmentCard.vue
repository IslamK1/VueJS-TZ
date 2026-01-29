<template>
  <div class="card h-100">
    <img :src="apartment.image" class="card-img-top" alt="Apartment" />

    <div class="card-body">
      <h6 class="card-title">
        {{ apartment.rooms }} комнаты • {{ apartment.area }} м²
      </h6>
      <p class="card-text">{{ apartment.address }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  apartment: Object
})
</script>
