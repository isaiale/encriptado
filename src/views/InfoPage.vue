<template>
  <div class="info">
    <h2>Información Detallada</h2>
    <p>Aquí hay más información sobre el sitio.</p>
    <img src="../assets/images/imagen-ejemplo.jpg" alt="Descripción de la imagen" />
    <router-link to="/">Regresar a Inicio</router-link>
  </div>
</template>

<script>
export default {
  name: 'InfoPage'
}
</script>

<style scoped>
.info {
  text-align: center;
  margin-top: 50px;
}

img {
  max-width: 100%;
  height: auto;
  margin-top: 20px;
}
</style>
