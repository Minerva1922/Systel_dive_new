<script>
  import logo from './assets/logo.png';
  import fondo from './assets/fondo.jpg';
  import QuienesSomos from './lib/QuienesSomos.svelte';
  let showMenu = false;

  function toggleMenu() {
    showMenu = !showMenu;
  }

</script>

<main style="background-image: url('{fondo}');">
  <img src={logo} alt="logo" class="logo" />
  
  <div class="menu-icon" on:click={toggleMenu}>
    ☰ 
  </div>

  {#if showMenu}
    <div class="overlay" on:click={toggleMenu}>
      <div class="menu" on:click={(e) => e.stopPropagation()}>
        <ul>
          <li><a href="quienessomos">Quiénes Somos</a></li>
          <li><a href="#">Qué Hacemos</a></li>
          <li><a href="#">Cámaras</a></li>
          <li><a href="#">Contacto</a></li>
        </ul>
      </div>
    </div>
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
    font-size: 24px; /* Tamaño del icono */
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
    align-items: flex-start; /* Alinea el menú desde arriba */
    justify-content: flex-end; /* Alinea el menú desde la izquierda si está abierto */
    overflow: hidden; /* Oculta el desbordamiento del menú cerrado */
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
    margin-bottom: 15px; /* Ajusta el espacio entre las opciones */
  }

  a {
    text-decoration: none;
    color: white;
    font-size: 16px;
  }
</style>