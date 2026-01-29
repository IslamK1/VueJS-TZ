<template>
  <div class="card p-3 mb-4">
    <h5 class="mb-3">Фильтры</h5>

    <div class="row g-2">
      <div class="col-6">
        <input
          type="number"
          class="form-control"
          placeholder="Площадь от"
          v-model.number="localFilters.areaFrom"
        />
      </div>

      <div class="col-6">
        <input
          type="number"
          class="form-control"
          placeholder="Площадь до"
          v-model.number="localFilters.areaTo"
        />
      </div>

      <div class="col-6">
        <input
          type="number"
          class="form-control"
          placeholder="Комнат от"
          v-model.number="localFilters.roomsFrom"
        />
      </div>

      <div class="col-6">
        <input
          type="number"
          class="form-control"
          placeholder="Комнат до"
          v-model.number="localFilters.roomsTo"
        />
      </div>

      <div class="col-12">
        <input
          type="text"
          class="form-control"
          placeholder="Поиск по адресу"
          v-model="localFilters.address"
        />
      </div>
    </div>
  </div>
</template>

<script setup>

import { reactive, watch } from 'vue'

const props = defineProps({
  filters: Object
})

const emit = defineEmits(['update'])

const localFilters = reactive({ ...props.filters })

watch(
  localFilters,
  () => emit('update', { ...localFilters }),
  { deep: true }
)
</script>
