<!-- Template que  define al componente -->
<template>
  <!-- Solo un DIV contenedor -->
  <div class="fondo">
    <!-- Título del contenido -->
    <h1 class="titulo">Personajes</h1>
    <!-- La directiva v-for permite recorrer el arreglo personajes -->   
    <div v-for="(p, i) in personajes" :key="i">
      <!-- Llamado al componente "personaje" pidiendo nombre e imagen para mostralos-->
      <personaje :src="p.picture" :name="p.nombre" />
    </div>
  </div>
</template>

<script>
// Importación componente hijo "personaje"
import personaje from "./components/Personaje";
export default {
  // Referencia a componente hijo "personaje"
  components: {
    personaje,
  },
  //Función data, retorna en un array el resultado de la función "mounted"
  data() {
    return {
      // Definimos un array vacío para guardar el resultado de la función "mounted"
      personajes: [],
    };
  },

  // Función mounted
  mounted() {
    // LLamo con fetch a la API rick y morty
    fetch("https://rickandmortyapi.com/api/character")
      // Espero la respuesta de la llamada como archivo json
      .then((response) => response.json())
      // Guardo los datos en formato json de la API en una variable llamada "data"
      .then((json) => {
        let data = json.results;
        // Con slice determino que solo traeré los 10 primeros elementos de la data, y mediante 
        // el recorrido de la misma con forEach extraigo solo los nombres e imágenes. 
        data.slice(0, 10).forEach((el) => {
          let nombre = el.name;
          let picture = el.image;
          // Mediante push envÍo al array personajes los objetos seleccionados de la data (nombres e imágenes).
          this.personajes.push({
            nombre,
            picture,
          });
        });
      })
      //Error en llamado a la data
      .catch((err) => {
        console.log(`Error ${err}`);
      });
  },
};
</script>

<!-- Estilo del componente -->
<style></style>
