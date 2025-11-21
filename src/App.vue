<script setup>
</script>

<template>
    <nav class="navbar">
      <RouterLink to="/" class="nav-link">🏠 Inici</RouterLink>
      <RouterLink to="/receptes" class="nav-link">🍜 Receptes</RouterLink>
    </nav>
    <RouterView />
</template>

<style scoped>
body {
  margin: 0px;
}
/* Reset básico */
html {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Barra de navegación */
.navbar {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 2rem;
  padding: 1rem 2rem;
  background-color: white;
  border-radius: 20px;
  position: sticky;
  top: 0;
  z-index: 1000;
  border: 1px solid black;
}

/* Links */
.nav-link {
  color: black;
  font-size: 1.2rem;
  font-weight: 600;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border-radius: 12px;
  transition: all 0.3s ease;
}

.nav-link:hover {
  background-color: rgba(255,255,255,0.2);
  transform: translateY(-2px);
}

/* Estado activo */
.router-link-active {
  background-color: rgba(255,255,255,0.3);
  color: orange;
  box-shadow: 0 4px 12px rgba(0,0,0,0.2);
}

/* Responsive */
@media (max-width: 600px) {
  .navbar {
    flex-direction: column;
    gap: 1rem;
    padding: 1rem;
  }

  .nav-link {
    font-size: 1rem;
    width: 100%;
    text-align: center;
  }
}
</style>
