<template>
  <div class="home">
    <h1 class="animated-title">Bienvenido a Mi Sitio</h1>
    <p>Un poco de información sobre este sitio.</p>
    <router-link to="/info">Más Información</router-link>
  </div>
</template>

<script>
export default {
  name: 'Home'
}
</script>

<style scoped>
.home {
  text-align: center;
  margin-top: 50px;
}

.animated-title {
  font-size: 2.5rem;
  animation: fadeIn 2s ease-in-out;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
</style>
