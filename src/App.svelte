<script>
  import { onMount } from 'svelte';
  import logo from './assets/logo.png';
  import fondo from './assets/fondo.jpg';
  import QuienesSomos from './lib/QuienesSomos.svelte';
  import QueHacemos from './lib/QueHacemos.svelte';
  import Camaras from './lib/Camaras.svelte';
  import Maletas from './lib/Maletas.svelte';

  let showMenu = false;
  let currentPage = null;
  let currentRoute = '';


  const routes = {
    'Quienes somos': QuienesSomos,
    'Que hacemos': QueHacemos,
    'Camaras': Camaras,
    'Maletas': Maletas,
  };

  function toggleMenu() {
    showMenu = !showMenu;
  }

  function navigate(route) {
    currentRoute = route;
    currentPage = routes[route];
    // toggleMenu(); // No cierres el menú al cambiar de página si deseas mantenerlo abierto
  }

  onMount(() => {
    const initialRoute = window.location.pathname.replace('/', ''); // Obtén la ruta inicial
    navigate(initialRoute || 'quienessomos'); // Navega a la ruta inicial o 'quienessomos'
  });
</script>

<main style="background-image: url('{fondo}');">
  <img src={logo} alt="logo" class="logo" on:click={() => navigate('/')} />

  <div class="menu-icon" on:click={toggleMenu}>
    ☰
  </div>

  {#if showMenu}
    <div class="overlay" on:click={toggleMenu}>
      <div class="menu" on:click={(e) => e.stopPropagation()}>
        <ul>
          {#each Object.keys(routes) as route}
            <li><a href={route} on:click={() => navigate(route)}>{route}</a></li>
          {/each}
        </ul>
      </div>
    </div>
  {/if}

  {#if currentRoute === 'quienessomos' && window.location.pathname === '/quienessomos'}
    <QuienesSomos />
  {:else}
    {#if currentPage}
      <svelte:component this={currentPage} />
    {/if}
  {/if}
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
    width: 50px;
    height: 60px;
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
    justify-content: flex-end;
    overflow: hidden;
  }

  .menu {
    width: 15%;
    height: 100%;
    background: rgba(0, 0, 0, 0.8);
    padding: 20px;
    color: white;
    text-align: center;
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
