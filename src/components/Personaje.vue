<!-- Template que  define al componente -->
<template>
  <!-- Solo un DIV contenedor -->
  <div class="contenido">
    <!-- Llamada a imagen -->
    <img class="imagen" :src="src" />
    <!-- Llamada a nombre -->
    <h3 class="nombre">{{ name }}</h3>
  </div>
</template>

<script>
// Componente personaje
export default {
  // Nombre del componente
  name: "personaje",
  // Propiedades pasadas de componente padre a componente hijo
  props: {
    src: String,
    name: String,
  },
};
</script>

<!-- Estilo del componente -->
<style></style>
