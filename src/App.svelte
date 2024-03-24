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
  import Mail from './assets/mail.ico'

  let showMenu = false;
  let currentRoute = '';

  // Definir las rutas y sus componentes asociados
  const routes = {
    'Quienes-somos': QuienesSomos,
    'Que-hacemos': QueHacemos,
    'Camaras': Camaras,
    'Equipo-cctv': EquipoCctv,
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
        <!-- Agrega el icono de correo -->
        <img src={Mail} alt="Correo" class="mail" />

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
    background-color: rgba(0, 0, 0, 0.7);
    padding: 60px;
    text-align-last: auto;
    overflow-y: auto; /* Habilita el scroll vertical */
    background-size: cover;
    height: 100vh;
    position: relative;
  }

  .logo {
    position: absolute;
    top: 10px;
    right: 10px;
    height: 15%;
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
    justify-content: flex-start;
    overflow: hidden;
  }

  .menu {
    width: 15%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8);
    padding: 10px;
    color: white;
    text-align: end;
    position: relative; 
    left: -100%; 
  }

  .menu.open {
    left: 0; 
    transition: left 0.3s ease; 
  }

  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  li {
    margin-top: 70px;
  }

  a {
    text-decoration: none;
    color: goldenrod;
    font-size: 25px;
    cursor: pointer;
  }

  .mail {
    margin-top: 20px;
    width: 50px;
    height: 50px;
  }
  


  </style>