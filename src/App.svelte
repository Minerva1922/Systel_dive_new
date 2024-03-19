<script>
// @ts-nocheck

  import { Router, Route } from 'svelte-routing';
  import { onMount } from 'svelte';
  import logo from './assets/logo.png';
  import fondo from './assets/fondo.jpg';
  import QuienesSomos from './lib/QuienesSomos.svelte';
  import QueHacemos from './lib/QueHacemos.svelte';
  import Camaras from './lib/Camaras.svelte';
  import EquipoCctv from './lib/EquipoCctv.svelte';

  let showMenu = false;
  let currentRoute = '';

  // Definir las rutas y sus componentes asociados
  const routes = {
    'quienes-somos': QuienesSomos,
    'que-hacemos': QueHacemos,
    'camaras': Camaras,
    'equipo-cctv': EquipoCctv,
  };

  // Función para alternar la visibilidad del menú
  function toggleMenu() {
    showMenu = !showMenu;
  }

  // Función para manejar la navegación
  function navigate(route) {
    currentRoute = route;
  }

  onMount(() => {
    // Obtener la ruta inicial
    const initialRoute = window.location.pathname || '/';
    navigate(initialRoute); // Navegar a la ruta inicial
  });
</script>

<main style="background-image: url('{fondo}')">
  <!-- Encabezado -->
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <img src={logo} alt="logo" class="logo" on:click={() => navigate('/')} />

  <!-- Icono del menú -->
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <div class="menu-icon" on:click={toggleMenu}>
    ☰
  </div>

  <!-- Menú desplegable -->
  {#if showMenu}
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div class="overlay" on:click={toggleMenu}>
      <div class="menu {showMenu ? 'open' : ''}" on:click={(e) => e.stopPropagation()}>
        <ul>
          {#each Object.keys(routes) as route}
            <li><a href="{route}" on:click={() => navigate(route)}>{route}</a></li>
          {/each}
        </ul>
      </div>
    </div>
    
  {/if}

  <!-- Router para manejar las rutas y renderizar los componentes correspondientes -->
  <Router>
    {#each Object.keys(routes) as route}
      <Route path={route} component={routes[route]} />
    {/each}
  </Router>
</main>


<style>
  main {
    background-size: cover;
    height: 100vh;
    position: relative;
  }

  .logo {
    position: absolute;
    top: 10px;
    right: 10px;
    height: 20%;
    z-index: 1;

  }

  .menu-icon {
    position: absolute;
    top: 10px;
    left: 10px;
    cursor: pointer;
    z-index: 1;
    color: white;
    font-size: 24px;
  
  }

  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    z-index: 2;
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
    overflow: hidden;
  }

  .menu {
    width: 15%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8);
    padding: 20px;
    color: white;
    text-align: center;
    position: relative; /* Añade esta línea */
    left: -100%; /* Añade esta línea */
  }

  .menu.open {
    left: 0; /* Añade esta línea */
    transition: left 0.3s ease; /* Añade esta línea */
  }

  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  li {
    margin-bottom: 15px;
  }

  a {
    text-decoration: none;
    color: white;
    font-size: 16px;
    cursor: pointer;
  }
</style>
