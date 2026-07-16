<script setup>
const props = defineProps({
  titulo: {
    type: String,
    required: true,
  },
  subtitulo: {
    type: String,
    required: true,
  },
})
</script>

<template>
  <header class="encabezado">
    <h1>{{ props.titulo }}</h1>
    <p>{{ props.subtitulo }}</p>
  </header>
</template>

<style scoped>
.encabezado {
  background: linear-gradient(135deg, #2563eb, #4f46e5);
  color: white;
  padding: clamp(1.25rem, 3vw, 2rem) clamp(1rem, 3vw, 2rem);
  text-align: center;
  border-radius: 0 0 1rem 1rem;
  box-shadow: 0 8px 24px rgba(37, 99, 235, 0.25);
}

.encabezado h1 {
  margin: 0;
  font-size: clamp(1.5rem, 3vw, 2rem);
}

.encabezado p {
  margin: 0.5rem 0 0;
  font-size: clamp(0.95rem, 2vw, 1rem);
  opacity: 0.95;
}
</style>
