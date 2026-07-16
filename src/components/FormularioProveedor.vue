<script setup>
import { ref } from 'vue'

const emit = defineEmits(['registrar'])

const empresa = ref('')
const contacto = ref('')
const telefono = ref('')
const correo = ref('')
const categoria = ref('')
const ciudad = ref('')
const mensaje = ref('')
const tipoMensaje = ref('')

function limpiarFormulario() {
  empresa.value = ''
  contacto.value = ''
  telefono.value = ''
  correo.value = ''
  categoria.value = ''
  ciudad.value = ''
}

function registrarProveedor() {
  if (
    !empresa.value.trim() ||
    !contacto.value.trim() ||
    !telefono.value.trim() ||
    !correo.value.trim() ||
    !categoria.value.trim()
  ) {
    mensaje.value = 'Complete todos los campos obligatorios.'
    tipoMensaje.value = 'error'
    return
  }

  const nuevoProveedor = {
    empresa: empresa.value.trim(),
    contacto: contacto.value.trim(),
    telefono: telefono.value.trim(),
    correo: correo.value.trim(),
    categoria: categoria.value,
    ciudad: ciudad.value.trim(),
  }

  emit('registrar', nuevoProveedor)
  limpiarFormulario()
  mensaje.value = 'Proveedor registrado correctamente.'
  tipoMensaje.value = 'success'
}
</script>

<template>
  <form class="formulario" @submit.prevent="registrarProveedor">
    <div class="campo">
      <label for="empresa">Nombre de la empresa *</label>
      <input id="empresa" v-model="empresa" type="text" placeholder="Ej. Distribuidora XYZ" />
    </div>

    <div class="campo">
      <label for="contacto">Nombre del contacto *</label>
      <input id="contacto" v-model="contacto" type="text" placeholder="Ej. Ana López" />
    </div>

    <div class="campo">
      <label for="telefono">Teléfono *</label>
      <input id="telefono" v-model="telefono" type="text" placeholder="Ej. 77712345" />
    </div>

    <div class="campo">
      <label for="correo">Correo electrónico *</label>
      <input id="correo" v-model="correo" type="email" placeholder="Ej. contacto@empresa.com" />
    </div>

    <div class="campo">
      <label for="categoria">Categoría *</label>
      <select id="categoria" v-model="categoria">
        <option value="">Seleccione una opción</option>
        <option value="Alimentos">Alimentos</option>
        <option value="Tecnología">Tecnología</option>
        <option value="Ropa">Ropa</option>
        <option value="Servicios">Servicios</option>
        <option value="Otros">Otros</option>
      </select>
    </div>

    <div class="campo">
      <label for="ciudad">Ciudad</label>
      <input id="ciudad" v-model="ciudad" type="text" placeholder="Ej. Santa Cruz" />
    </div>

    <button type="submit">Registrar proveedor</button>

    <p v-if="mensaje" :class="['mensaje', tipoMensaje]">{{ mensaje }}</p>
  </form>
</template>

<style scoped>
.formulario {
  display: grid;
  gap: 1rem;
  background: white;
  padding: clamp(1rem, 2.5vw, 1.5rem);
  border-radius: 1rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
}

.campo {
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  min-width: 0;
}

label {
  font-weight: 600;
  color: #1f2937;
}

input,
select,
button {
  width: 100%;
  border: 1px solid #d1d5db;
  border-radius: 0.6rem;
  padding: 0.75rem;
  font: inherit;
}

button {
  background: #2563eb;
  color: white;
  cursor: pointer;
  border: none;
  font-weight: 700;
}

button:hover {
  background: #1d4ed8;
}

.mensaje {
  margin: 0;
  font-weight: 600;
}

.mensaje.error {
  color: #dc2626;
}

.mensaje.success {
  color: #15803d;
}

@media (min-width: 700px) {
  .formulario {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .campo,
  button,
  .mensaje {
    grid-column: span 1;
  }

  button,
  .mensaje {
    grid-column: 1 / -1;
  }
}
</style>
