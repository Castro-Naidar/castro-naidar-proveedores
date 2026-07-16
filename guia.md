# PRIMER EXAMEN PARCIAL

## Programación Web II — Grupo Mañana

**Modalidad:** Práctica individual  
**Tiempo sugerido:** 1 hora y 30 minutos  
**Puntaje total:** 20 puntos

---

# Caso práctico: Registro de proveedores

Una microempresa de Santa Cruz de la Sierra necesita una página web sencilla para registrar a sus proveedores. Actualmente, la información se anota manualmente, lo que dificulta consultar los datos y mantenerlos organizados.

El estudiante deberá crear desde cero una aplicación en Vue.js que permita ingresar la información de los proveedores mediante un formulario y mostrar los registros en la misma página. El proyecto deberá incluir un componente reutilizable para el encabezado y publicarse en un repositorio de GitHub.

---

# Instrucciones generales

1. El proyecto debe crearse desde cero utilizando Vue.js.
2. La aplicación debe ejecutarse correctamente con `npm run dev`.
3. El encabezado debe desarrollarse como un componente independiente y reutilizable.
4. El formulario debe almacenar temporalmente los datos en memoria.
5. No es necesario utilizar base de datos ni backend.
6. El proyecto deberá subirse a un repositorio de GitHub.
7. El estudiante deberá realizar como mínimo dos commits.
8. El enlace del repositorio será el medio oficial de entrega.
9. No se aceptarán proyectos comprimidos como sustitución del repositorio.

---

# PARTE I. Creación y configuración del proyecto (3 puntos)

Crear un proyecto nuevo de Vue.js con el siguiente nombre:

```text
apellido-nombre-proveedores
```

Ejemplo:

```text
castro-naidar-proveedores
```

Para crear el proyecto:

```bash
npm create vue@latest
```

Seleccionar una configuración básica:

- TypeScript: No
- JSX: No
- Vue Router: No
- Pinia: No
- Pruebas: No
- ESLint: Sí
- Prettier: Opcional

Luego ejecutar:

```bash
cd apellido-nombre-proveedores
npm install
npm run dev
```

## Se evaluará

- Creación correcta del proyecto.
- Ejecución sin errores.
- Organización básica de carpetas.
- Eliminación del contenido de demostración que no sea necesario.

---

# PARTE II. Componente reutilizable de encabezado (4 puntos)

Crear el archivo:

```text
src/components/EncabezadoApp.vue
```

El componente deberá recibir mediante **props**:

- `titulo`
- `subtitulo`

El componente debe mostrar ambos valores en la parte superior de la página.

Desde `App.vue`, utilizarlo de la siguiente manera:

```vue
<EncabezadoApp
  titulo="Registro de Proveedores"
  subtitulo="Sistema de apoyo para la gestión comercial"
/>
```

## Requisitos

- El componente debe estar en un archivo independiente.
- Debe ser importado correctamente en `App.vue`.
- Los textos no deben estar escritos directamente dentro del componente.
- Debe utilizar `defineProps()`.
- Debe tener estilos básicos mediante `<style scoped>`.

---

# PARTE III. Formulario de registro (6 puntos)

Crear el componente:

```text
src/components/FormularioProveedor.vue
```

El formulario deberá contener los siguientes campos:

| Campo                | Tipo sugerido     |
| -------------------- | ----------------- |
| Nombre de la empresa | Texto             |
| Nombre del contacto  | Texto             |
| Teléfono             | Texto             |
| Correo electrónico   | Correo            |
| Categoría            | Lista desplegable |
| Ciudad               | Texto             |

La categoría deberá permitir seleccionar una de estas opciones:

- Alimentos
- Tecnología
- Ropa
- Servicios
- Otros

También deberá incluir un botón:

```text
Registrar proveedor
```

## Requisitos técnicos

El formulario debe utilizar:

- `ref()`
- `v-model`
- `@submit.prevent` o `@click`
- Una función para registrar la información
- Limpieza de campos después del registro

El formulario **no deberá recargar la página**.

---

# PARTE IV. Validaciones y mensajes (2 puntos)

Antes de registrar un proveedor, validar que:

- El nombre de la empresa no esté vacío.
- El nombre del contacto no esté vacío.
- El teléfono no esté vacío.
- El correo no esté vacío.
- Se haya seleccionado una categoría.

Cuando falten datos, mostrar un mensaje visible:

```text
Complete todos los campos obligatorios.
```

Cuando el registro sea correcto, mostrar:

```text
Proveedor registrado correctamente.
```

> No se permite utilizar solamente `alert()` como forma de validación. El mensaje debe aparecer dentro de la interfaz.

---

# PARTE V. Listado dinámico de proveedores (3 puntos)

Los proveedores registrados deberán mostrarse debajo del formulario.

Puede utilizarse una **tabla** o **tarjetas**.

La información mínima que debe mostrarse es:

- Empresa
- Contacto
- Teléfono
- Correo
- Categoría
- Ciudad

Utilizar:

```text
v-for
```

Cuando no existan proveedores registrados, mostrar:

```text
No existen proveedores registrados.
```

Utilizar:

- `v-if`
- `v-else`
- `v-show`

---

# PARTE VI. Git y GitHub (2 puntos)

Crear un repositorio en GitHub con el mismo nombre del proyecto:

```text
apellido-nombre-proveedores
```

## Primer commit

Después de crear y limpiar el proyecto.

## Segundo commit

```bash
git commit -m "Agregar encabezado y registro de proveedores"
```

El repositorio debe contener:

- Código fuente completo.
- Componente `EncabezadoApp.vue`.
- Componente `FormularioProveedor.vue`.
- Archivo `App.vue`.
- Como mínimo dos commits.
- Un archivo `README.md`.

---

# Contenido mínimo del README.md

```md
# Registro de Proveedores

## Estudiante

Nombre completo

## Descripción

Aplicación desarrollada en Vue.js para registrar y mostrar proveedores.

## Funcionalidades

- Encabezado reutilizable
- Formulario de registro
- Validación de datos
- Listado dinámico

## Tecnologías

- Vue.js
- JavaScript
- HTML
- CSS
- Git
- GitHub
```

---

# Estructura esperada

```text
apellido-nombre-proveedores/
├── src/
│   ├── components/
│   │   ├── EncabezadoApp.vue
│   │   └── FormularioProveedor.vue
│   ├── App.vue
│   └── main.js
├── package.json
└── README.md
```
