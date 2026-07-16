<script setup>
import { ref } from 'vue'
import EncabezadoApp from './components/EncabezadoApp.vue'
import FormularioProveedor from './components/FormularioProveedor.vue'

const proveedores = ref([])

function agregarProveedor(nuevoProveedor) {
  proveedores.value.push(nuevoProveedor)
}
</script>

<template>
  <div class="app">
    <EncabezadoApp
      titulo="Registro de Proveedores"
      subtitulo="Sistema de apoyo para la gestión comercial"
    />

    <main class="contenido">
      <FormularioProveedor @registrar="agregarProveedor" />

      <section class="lista">
        <h2>Proveedores registrados</h2>

        <div v-if="proveedores.length" class="tabla">
          <div v-for="(proveedor, index) in proveedores" :key="index" class="fila">
            <p><strong>Empresa:</strong> {{ proveedor.empresa }}</p>
            <p><strong>Contacto:</strong> {{ proveedor.contacto }}</p>
            <p><strong>Teléfono:</strong> {{ proveedor.telefono }}</p>
            <p><strong>Correo:</strong> {{ proveedor.correo }}</p>
            <p><strong>Categoría:</strong> {{ proveedor.categoria }}</p>
            <p><strong>Ciudad:</strong> {{ proveedor.ciudad || 'No especificada' }}</p>
          </div>
        </div>

        <p v-else class="vacio">No existen proveedores registrados.</p>
      </section>
    </main>
  </div>
</template>

<style scoped>
.app {
  min-height: 100vh;
  background: #f8fafc;
}

.contenido {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding: clamp(1rem, 3vw, 2rem) clamp(1rem, 3vw, 2rem) 3rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.lista {
  width: 100%;
  background: white;
  padding: clamp(1rem, 2.5vw, 1.5rem);
  border-radius: 1rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  overflow: hidden;
}

.lista h2 {
  margin-top: 0;
  color: #1f2937;
}

.tabla {
  display: grid;
  gap: 1rem;
}

.fila {
  border: 1px solid #e5e7eb;
  border-radius: 0.8rem;
  padding: 1rem;
  background: #f9fafb;
}

.fila p {
  margin: 0.3rem 0;
  overflow-wrap: anywhere;
}

.vacio {
  color: #6b7280;
  font-style: italic;
}

@media (min-width: 900px) {
  .contenido {
    grid-template-columns: minmax(0, 1.05fr) minmax(0, 0.95fr);
    align-items: start;
  }
}
</style>
