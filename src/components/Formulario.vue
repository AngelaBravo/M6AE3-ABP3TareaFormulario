<template>
  <div class="container py-4">
    <h2 class="mb-4">Selecciona tu tipo de estudios</h2>
    <div class="mb-3">
      <div class="form-check" v-for="opcion in opcionesEstudios" :key="opcion.value">
        <input class="form-check-input" type="radio" :id="opcion.value" :value="opcion.value" v-model="estudios">
        <label class="form-check-label" :for="opcion.value">
          {{ opcion.label }}
        </label>
      </div>
    </div>
    <div class="alert alert-info">Opción seleccionada: <strong>{{ estudiosLabel }}</strong></div>

    <h2 class="mb-4 mt-5">Selecciona un día de la semana</h2>
    <div class="mb-3">
      <select class="form-select" v-model="dia">
        <option disabled value="">Selecciona un día</option>
        <option v-for="d in diasSemana" :key="d" :value="d">{{ d }}</option>
      </select>
    </div>
    <div class="alert alert-info">Día seleccionado: <strong>{{ dia || 'Ninguno' }}</strong></div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const opcionesEstudios = [
  { value: 'primarios', label: 'Primarios' },
  { value: 'secundarios', label: 'Secundarios' },
  { value: 'universitarios', label: 'Universitarios' },
  { value: 'posgrado', label: 'Posgrado' }
]

const estudios = ref('universitarios')
const dia = ref('')

const diasSemana = [
  'Lunes',
  'Martes',
  'Miércoles',
  'Jueves',
  'Viernes',
  'Sábado',
  'Domingo'
]

const estudiosLabel = computed(() => {
  const found = opcionesEstudios.find(o => o.value === estudios.value)
  return found ? found.label : ''
})
</script>

<style scoped>
.container {
  max-width: 500px;
}
</style>
